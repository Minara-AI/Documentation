# Create Cross-sectional Strategies

> Build market-neutral, AI-generated quant strategies in Minara.\
> Live at [https://minara.ai/app/xstrategy](https://beta.minara.ai/app/xstrategy)

***

### What is a cross-sectional strategy?

A cross-sectional strategy is defined by _how_ it makes a decision, in contrast to a **time-series** strategy:

* A **time-series** strategy looks at _one asset against its own history_ and asks "is BTC going up or down from here?". It's an absolute, directional call on each asset.
* A **cross-sectional** strategy looks at _an universe (a pool of assets) against each other at the same moment_ and asks "which assets rank highest, and which rank lowest, **under my scoring rule**?". It's a relative call.

The cross-sectional strategy then takes a **direction** you choose: **long-only** (buy the top-ranked assets), **short-only** (sell the bottom-ranked ones), or **long-short** (do both at once).

The long-short version is what people mean by **market-neutral**: it holds roughly balanced long and short baskets, so the broad market's up-or-down move (**beta** volatility) partially cancels out between the two legs. What's left is the gap between the top basket and the bottom basket, which is the **alpha** your strategy is trying to capture.

In other words, a cross-sectional long-short strategy aims to earn alpha while staying relatively independent of beta. (A long-only or short-only version keeps beta exposure and is not market-neutral.) The market-neutral approach is a hedge-fund staple: typically lower volatility and steadier than a directional bet.

One line to keep the two strategy types straight: a **time-series** strategy solves _timing_: **when** to go long or short a given asset. A **cross-sectional** strategy solves _selection_: **which** assets to hold long or short at any given moment.

#### "Stronger / weaker" in terms of ranking

**"Stronger"** means "scores higher under the ranking rule _you_ defined." The ranking rule is whatever scoring system you build out of factors:

* If your rule is _"find undervalued quality assets with upside potential,"_ then the asset that best fits that description is the "strongest", even if its price looks bottomed.
* If your rule is _"find the assets with the fastest recent momentum,"_ then "strongest" does lean toward recent winners.

So strong/weak is **relative, and entirely a function of your ranking definition**.

***

### How the system works

A **factor** is a rule that turns each asset into a score. The same rule is applied to every asset in the universe, so the scores can be compared and ranked. For example:

* _"return over the past 5 days"_ scores recent momentum,
* _"debt growth over 3 years"_ scores balance-sheet quality,
* _"MACD normalized by price"_ scores trend strength on a price-comparable scale.

A cross-sectional strategy combines one or more factors into a single combined score per asset, then:

1. **Rank** every asset in the universe by the combined factor score.
2. **Long** the top slice (e.g. top 5) and/or **Short** the bottom slice (e.g. bottom 5).
3. **Rebalance** on a schedule (every 4h, daily, 3d, etc.).

Each factor in Minara's library has already passed an objective quality screen: IC (information coefficient), turnover, fee resilience, regime stability, monotonicity, and so on. Factors that fail the screen are not presented.

***

### Building a strategy end-to-end

#### Step 1. Describe

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

1. Make sure the mode toggle says **Multi-Asset**.
2. Pick your **universe**. It defaults to **TradFi 30**; click another universe card (Coin 30 / Coin 50) to switch. You may also see the detailed asset list by clicking on the universe.&#x20;
3. Give the AI your input. You can do **any** of these:
   * **Factors + prompt.** Click factor cards in the library to add them, then add a line of guidance. E.g. select **3-Year Debt Growth (inverted)** and **MACD (Price-Normalized)**, then write _"combine these, long the top 5 and short the bottom 5."_
   * **Factors only.** Simply pick factors from the library, just let Minara builds a strategy around them.
   * **Plain description only.** Examples:
     * _"Buy the stocks that have been going up the most lately, and short the ones falling the most."_
     * _"Pick the strongest coins each week and short the weakest ones."_
4. Send it to Minara. The flow moves to **AI Coding** and a backtest runs automatically.

#### Step 2. AI Coding

The AI translates your description into **readable Python code** (which can be found in the "code" section).

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

* Factor imports are pulled from the validated library.
* The logic is fully visible: rebalance schedule, ranking method, position sizing, missing-value handling.
* You can always **edit the code directly**, which will create a new version upon saving.&#x20;
* Though you can also iterate your strategy simply through the chat ("change rebalance frequency to every 3 days", "swap MACD for short-term reversal").

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

#### Step 3. Backtest

Minara automatically backtests the generated strategy on the window of last 4 years by default. You may also tweak the parameters and backtest manually.

**Common parameters**

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

* You may change universe, leverage, interval (certain avalaible options) and the backtest window.
* Pick the direction amongst these options: Long Only (only long the top assets), Short Only (only short the bottom assets), Long & Short (long the top and short the bottom).
* Select the way you pick: X symbols (e.g. long top 3 and short bottom 3) or by percentage (e.g. only long the top 5% within the universe).
* Select the weighting mode: equal-weighted means same sizing for every position; signal-weighted means sizing the position by the asset's score.
* **The inverted score** option flips the ranking so the _lowest_-scoring assets become the top picks. Turn it on when your factor is "lower = better" (e.g. cheap valuation, low debt growth) and your code didn't already negate it — otherwise the strategy would bet the wrong way.

**Advance settings**

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="249">Name</th><th width="249.2559814453125">Function</th><th>Use case</th></tr></thead><tbody><tr><td><strong>Initial capital</strong></td><td>Starting capital the backtest deploys. The equity curve and all returns are measured against this. </td><td>Important when the strategy trade using cash instead of percentage. (e.g. "buy $200 each time")</td></tr><tr><td><strong>Taker fee</strong></td><td>The trading fee charged on each fill, in basis points (<code>1 bp = 0.01%</code>). <strong>Toggle on</strong> = charge this fee; <strong>toggle off</strong> = run the backtest fee-free.</td><td>Turn off only to see the gross (pre-fee) picture. Raise it to stress-test a high-turnover strategy against worse fees. Keep it on for any realistic result.</td></tr><tr><td><strong>Slippage</strong></td><td>An extra cost, in basis points, added on top of the taker fee on every fill, simulating the gap between the price you expect and the price you actually get. Effective per-fill cost = taker fee + slippage (e.g. 2 bps fee + 3 bps slippage = 5 bps total).</td><td>Raise it to be conservative. Especially for larger size, thinner assets, or higher-frequency rebalancing, where real fills drift further from the quoted price.</td></tr><tr><td><strong>Rebalance tolerance</strong></td><td>A "don't bother" band. If an asset's new target weight differs from its current weight by <strong>less than this</strong>, the strategy holds the position as-is instead of trading. "This position <em>barely changed</em>, don't re-trade it"</td><td>Raise it (e.g. 0.3–0.5%) to trade less and cut fees on a high-turnover strategy. Lower it toward 0 to track target weights more tightly.</td></tr><tr><td><strong>Weight floor</strong></td><td>A minimum-size filter. Any target weight <strong>smaller than this in absolute value</strong> is set to zero. "This position is <em>too small</em>, don't open it"</td><td>Raise it to hold fewer, larger positions (cleaner book, lower fees). Lower it to allow more small positions.</td></tr><tr><td><strong>Warmup bars</strong></td><td>How many leading bars to use just to "warm up" indicators before trading starts (e.g. a 200-day moving average needs 200 bars of history before its first valid value). These bars prime the indicators and are excluded from performance.</td><td>Increase it if your strategy uses long-lookback indicators and you want to be sure the early backtest period isn't trading on half-formed signals.</td></tr></tbody></table>

**Backtest Report**

Minara backtests the strategy on historical data:

* **TradFi:** FMP data.
* **Crypto:** Binance Futures data.

<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

**Headline metrics (top row)**

<table><thead><tr><th width="189.564208984375">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Total Return</strong></td><td>Total % gain over the whole backtest window, plus the dollar value of the final balance.</td></tr><tr><td><strong>CAGR</strong></td><td>Compound annual growth rate: the return <em>annualized</em> on a 365-day basis, so windows of different lengths are comparable.</td></tr><tr><td><strong>Max Drawdown</strong></td><td>The worst peak-to-trough drop in equity over the period. Your single best gauge of "how much pain to sit through."</td></tr><tr><td><strong>Total Fills</strong></td><td>Number of rebalance fills (individual order executions) across the run.</td></tr><tr><td><strong>Sharpe Ratio</strong></td><td>Risk-adjusted return: return per unit of <em>total</em> volatility. Higher is better; >1 is decent, >2 is strong.</td></tr><tr><td><strong>Calmar Ratio</strong></td><td>CAGR ÷ |Max Drawdown|. Return earned per unit of worst-case pain.</td></tr><tr><td><strong>Alpha</strong></td><td>Annualized excess return vs. the benchmark, after stripping out market movement (CAPM intercept). Benchmark is <strong>SPY (S&#x26;P 500)</strong> for TradFi, <strong>BTC</strong> for crypto. This is the "skill" component.</td></tr><tr><td><strong>Beta</strong></td><td>How much the strategy moves with the benchmark. ~0 = market-neutral; 1 = moves one-for-one with the market; >1 = amplified. A long-short strategy should sit near 0; a long-only one will be higher.</td></tr></tbody></table>

**Charts**

* **Strategy equity:** your equity curve (solid line) vs. buy-and-hold the benchmark (dashed line). The gap between them is your outperformance.
* **Drawdown:** the underwater chart: how far below its prior peak the strategy was at every point. Deep, long troughs are the periods you'd have had to endure.

**Tabs: Overview · Per-Symbol PnL · Trades**

* **Overview:** the aggregate stats below.
* **Per-Symbol PnL:** profit/loss broken down by each asset, so you can see which names carried the strategy and which dragged.
* **Trades:** the individual trade log.

**Overview - Composition**

A treemap of **trading volume by symbol** — bigger tiles = more turnover in that name. Quickly shows whether the strategy is concentrated in a few assets or spread across the universe.

**Overview - Returns**

<table><thead><tr><th width="235.3150634765625">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Gross profit / %</strong></td><td>Total made by all winning trades (before netting losses).</td></tr><tr><td><strong>Gross loss / %</strong></td><td>Total lost by all losing trades.</td></tr><tr><td><strong>Profit factor</strong></td><td>Gross profit ÷ gross loss. >1 means winners outweigh losers; the higher the better.</td></tr><tr><td><strong>Expected payoff</strong></td><td>Average profit per closed trade (net).</td></tr><tr><td><strong>Commission paid</strong></td><td>Total fees paid over the run (already deducted from returns).</td></tr></tbody></table>

**Overview - Risk & benchmark**

<table><thead><tr><th width="239.2083740234375">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Sortino</strong></td><td>Like Sharpe, but only penalizes <em>downside</em> volatility — ignores upside swings. Often a fairer read for asymmetric strategies.</td></tr><tr><td><strong>Buy-and-hold return</strong></td><td>What you'd have made just holding the benchmark over the same window — the bar to beat.</td></tr><tr><td><strong>Strategy outperformance</strong></td><td>How much the strategy beat (or lagged) buy-and-hold.</td></tr><tr><td><strong>Final balance</strong></td><td>Ending equity in dollars.</td></tr></tbody></table>

**Overview - Trade analysis (based on closed positions)**

<table><thead><tr><th width="212.5546875">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Closed positions</strong></td><td>Number of completed (opened-and-closed) trades — your sample size. Bigger = more statistically trustworthy.</td></tr><tr><td><strong>Win rate</strong></td><td>Share of closed trades that were profitable.</td></tr><tr><td><strong>Win/loss ratio</strong></td><td>Average win size ÷ average loss size. >1 means your wins are bigger than your losses.</td></tr><tr><td><strong>Avg win / Avg loss</strong></td><td>Average dollar gain on winners / average dollar loss on losers.</td></tr><tr><td><strong>Avg holding period</strong></td><td>Average number of bars a position is held (a "bar" is one rebalance interval — e.g. with daily rebalancing, ~41 bars ≈ 41 days).</td></tr></tbody></table>

> A high win rate with a low win/loss ratio (many small wins, few big losses) and the reverse (few big wins, many small losses) can both be healthy. Always read win rate and win/loss ratio _together._

**Overview - Portfolio**

<table><thead><tr><th width="274.6119384765625">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Universe size</strong></td><td>How many assets the strategy could choose from.</td></tr><tr><td><strong>Avg symbols held</strong></td><td>Average number of positions open at once.</td></tr><tr><td><strong>Long / Short / Net exposure</strong></td><td>Share of capital on the long side, the short side, and the difference. <strong>Net ≈ 0% = market-neutral</strong>; Net = 100% long, 0% short = a long-only strategy (and explains a higher Beta).</td></tr><tr><td><strong>Avg position size</strong></td><td>Average dollar size of a single position.</td></tr><tr><td><strong>Closed notional</strong></td><td>Total traded volume across all closed positions.</td></tr></tbody></table>

Iterate by chatting with the AI to refine. Each refinement re-runs the backtest.

#### Step 4. Live Trading

Once you are satisfied with the strategy, you can start running it live. Push it to a dedicated sub-wallet on the underlying venue:

* **Crypto** routes through **Lighter** or **Hyperliquid**.
* **TradFi** routes through **Hyperliquid**.

A deployed strategy appears in the left sidebar with a `Deployed` tag, and also visible in the trade-perps page. You can stop it at any time.



***

### FAQ

**Is the AI a black box?**\
No. Open the Code tab — the strategy is plain Python with named factor imports. AI does the assembly; the factors and the screen are pre-vetted.

**Is the backtest realistic?**\
Returns are reported after fees, and slippage is included as a configurable per-fill cost on top of fees (see Strategy settings). Real-world fills and capacity limits still won't match a backtest exactly, but we continue to iterate our engine to get closer to it.

**Does this depend on the market going up or down?**\
It depends on the direction you choose:

* **Long-short** is the market-neutral case. It holds roughly equal long and short positions, so if the whole market drops 5%, both legs drop \~5% and the spread stays. It makes money when the longs outperform the shorts, regardless of whether the market is up or down.
* **Long-only** and **short-only** are _not_ market-neutral. They keep full exposure to market direction (beta): a long-only book still loses if the whole market falls, and a short-only book still loses if it rises. With these, you're betting that you've selected the right direction aligning with the market's overall move.

**What data feeds the backtests?**\
Binance for crypto. FMP for TradFi.

**The platform trade RWA tradfi perps, why backtest on FMP data instead?**\
The tokenized (RWA) contracts on Hyperliquid are still young and don't have enough price history for a trustworthy backtest. Quant validation needs _long_ history to avoid short-term overfitting, so we deliberately use FMP, which provides decades of stock data. The trade-off: Hyperliquid's actual price, order flow, and liquidity will differ from the FMP series. So please treat the backtest as directional evidence, not a promise, and mind the risk when you go live.

**Can professional quants get something out of this?**\
Yes. Reasons including:

1. Natural-language sketching to validate an idea or factor in minutes, not days.
2. No need to build your own backtest infrastructure.

