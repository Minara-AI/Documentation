# Create Time-series Strategies

> Build directional, AI-generated trading strategies in Minara.\
> Live at [strategy.minara.ai ](https://minara.ai/app/strategy-studio)

### What is a time-series strategy?

A time-series strategy is defined by _how_ it makes a decision. A **time-series** strategy looks at _one asset against its own history_ and asks "is BTC going up or down from here? Is now the moment to long, short, or not to trade?". It's an absolute, directional call.

A time-series strategy trades one symbol (e.g. BTC, ETH, GOLD). Instead of ranking assets, it watches that asset's own price, volume, and indicators over time and fires **entry** and **exit** signals: for example, open a long when a breakout confirms, close it when a stop is hit or the trend reverses.

A **time-series** strategy solves _timing_: **when** to go long or short a given asset.&#x20;

#### "Signal" in terms of timing

A time-series strategy is built from **signals**: conditions on the asset's own series that flip you into or out of a position:

* If your rule is _"go long when price breaks above the 20-day high, exit on a 3% stop,"_ the breakout is your entry signal and the stop is your exit signal.
* If your rule is _"buy when RSI drops below 30, sell when it crosses back above 50,"_ the oversold reading is your entry and the mean-reversion cross is your exit.

So the whole strategy is **a set of timing rules on one asset's history.**

***

### How the system works

An **indicator** is a rule that turns the asset's price/volume history into a value you can test: a moving average, RSI, MACD, Bollinger Bands, ATR, and so on. A time-series strategy combines one or more indicators into **entry** and **exit** conditions, then:

1. **Watch** the asset bar-by-bar on your chosen timeframe (15m, 1h, 4h, daily…).
2. **Enter** long or short when your entry condition fires.
3. **Exit** on a take-profit, stop-loss, trailing stop, or a signal-based reversal.
4. **Repeat** for the life of the strategy.

{% columns %}
{% column width="50%" %}
<figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

Signaly visually presented on the chart
{% endcolumn %}

{% column width="50%" %}
<figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

Trade one by one listed
{% endcolumn %}
{% endcolumns %}

***

### The screen on first load

When you open **Strategy Studio**, you see:

<figure><img src="../../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>

#### 1. Left sidebar — your strategy list

* **New Strategy** button to start a fresh strategy.
* **Time-Series / Cross-Sectional** toggle, Time-Series by default.  (Check out cross-sectional strategies: [create-cross-sectional-strategies.md](create-cross-sectional-strategies.md "mention"))
* Strategy tags: your saved strategies, with lifecycle status (`Draft`, `Deployed`, `Published`, `Running`) and last-modified time.

#### 2. Prompt box + creation methods

Below the header is your **prompt box** with the **Time-Series / Cross-Sectional** mode toggle. A time-series strategy just needs **one asset and a timeframe,** the AI infers these from your description, or you set them explicitly.

Ways to seed a strategy:

| Method               | UI                                                                            | Best for                     | What you do                                                                          |
| -------------------- | ----------------------------------------------------------------------------- | ---------------------------- | ------------------------------------------------------------------------------------ |
| **Natural language** | <img src="../../.gitbook/assets/image (128).png" alt="" data-size="original"> | Anyone                       | Describe the idea in plain words.                                                    |
| **Quick Questions**  | <img src="../../.gitbook/assets/image (129).png" alt="" data-size="original"> | Beginners                    | Pick a curated question and edit on top of it as you prefer.                         |
| **Templates**        | <img src="../../.gitbook/assets/image (130).png" alt="" data-size="original"> | Anyone starting fast         | Pick a curated template with real backtest data, then answer a few questions.        |
| **Form builder**     | <img src="../../.gitbook/assets/image (131).png" alt="" data-size="original"> | Traders who know indicators  | Select pair, timeframe, style, and indicators from menus.                            |
| **Video builder**    | <img src="../../.gitbook/assets/image (132).png" alt="" data-size="original"> | Traders with video materials | Simply upload the video about your trading strategy for AI to transribe and analyze. |
| **Code import**      | <img src="../../.gitbook/assets/image (133).png" alt="" data-size="original"> | Developers                   | Paste PineScript; Minara transpiles it.                                              |

### Building a strategy end-to-end

#### Step 1. Describe

1. Make sure the mode toggle says **Time-Series**.
2. Give the AI your input. You can do **any** of these:
   * **Plain-English description only.** Say what you want in everyday words:
     * _"Create a BTC trend-following strategy on the 4h timeframe."_
     * _"Long ETH when it breaks above resistance, with a 3% stop loss."_
     * _"Mean-reversion on SOL: buy when RSI drops below 30, sell when it recovers to 50."_
   * **Image or video.** Upload a marked-up chart screenshot and let AI read your annotations, or a short video explaining the idea.
   * **Form builder.** Click **Form** to pick pair, timeframe, style, and indicators from menus — AI assembles the prompt.
   * **Code import.** Click **Code** to paste PineScript; AI converts it to Minara's execution format, preserving your logic.
3. Send your input. Minara asks a clarifying question or two if needed, then moves to **AI Coding** and runs a backtest automatically.

{% columns %}
{% column %}
<figure><img src="../../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>

Example: natural language input
{% endcolumn %}

{% column %}
<figure><img src="../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

Example: form builder input
{% endcolumn %}
{% endcolumns %}

#### Step 2. AI Coding

The AI translates your description into **readable code**:

* The full logic is visible: entry conditions, exit conditions (stop-loss / take-profit / trailing / signal reversal), position actions (open, add, reduce, close), and indicator parameters.&#x20;
* You can **edit the code directly** before backtesting; the chat is the recommended way to iterate ("switch to a 2% trailing stop", "add a volume filter", "use EMA crossover instead of RSI").

The "no black box" property comes from this stage: AI generates the assembly, but the output is plain code you (or anyone you share it with) can read and change.

{% columns %}
{% column %}
![](<../../.gitbook/assets/image (140).png>)

View desc and code
{% endcolumn %}

{% column %}
<figure><img src="../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

Edit code: this creates a new version&#x20;
{% endcolumn %}
{% endcolumns %}

#### Step 3. Backtest

Backtest runs automatically once code is ready, you may also manually tweak the backtest parameters and backtest it again. Minara backtests the strategy on that asset's historical candles:

* **Crypto:** Binance data.
* **TradFi (incl. US stocks, metals):** FMP data.

**Common parameters**

<figure><img src="../../.gitbook/assets/image (145).png" alt=""><figcaption></figcaption></figure>

| Parameter                | What it does                                                                            | When to change it                                                                  |
| ------------------------ | --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Asset**                | Which single symbol to trade.                                                           | Test the same logic on a different asset.                                          |
| **Timeframe (interval)** | Candle interval (15m, 1h, 4h, daily…).                                                  | The same logic behaves very differently across timeframes.                         |
| **Time Window**          | How much history to load. Longer window = ,ore candles = more robust result.            | Use a longer window to reduce overfitting.                                         |
| **Fees**                 | Per-fill trading cost and the extra gap between expected and actual fill price, in bps. | Keep fees on for realism; raise slippage to stress-test high-frequency strategies. |

**Advance settings**

<figure><img src="../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

**Advanced:** open the setting section for fine control over how the backtest fills orders and sizes positions.&#x20;

<table><thead><tr><th width="200.40625">Setting</th><th>What it does</th><th>When to change it</th></tr></thead><tbody><tr><td><strong>Fees</strong></td><td>Toggle between the venue (Hyperliquid/Lighter) fee preset and <strong>Custom</strong> rates. Pick to model the venue you'll actually deploy on; pick <strong>Custom</strong> to enter your own.</td><td>Use the venue option for a realistic live estimate; Custom to stress-test other fee levels.</td></tr><tr><td><strong>Taker Fee Rate</strong></td><td>Fee charged when your order crosses the spread (takes liquidity). i.e. most strategy fills.</td><td>Raise it to stress-test a high-turnover strategy against worse fees.</td></tr><tr><td><strong>Maker Fee Rate</strong></td><td>Fee charged when your order adds liquidity (rests on the book before filling).</td><td>Adjust to match the venue you'll trade on.</td></tr><tr><td><strong>Initial Capital</strong></td><td>Starting capital the backtest deploys, in USD. All returns are measured against it.</td><td>Important when the strategy trade using cash instead of percentage. (e.g. "buy $200 each time")</td></tr><tr><td><strong>Pyramiding</strong></td><td>The maximum number of entries allowed in the <em>same direction</em> before you must exit. i.e. how many times the strategy can add to a position. <code>1</code> = no adding.</td><td>Raise it to let a winning position scale in; keep low to avoid over-concentration.</td></tr><tr><td><strong>Slippage</strong></td><td>An extra cost added on top of the fee on every fill, modeling the gap between the price you expect and the price you get.</td><td>Raise it to be conservative. Larger size, thinner assets, or higher-frequency rebalancing drift further from the quote.</td></tr></tbody></table>

All numbers are **after fees** (and slippage according to your settings). Results appear in two tabs: **Metrics** and **Trades**.

**Metrics — headline row (always visible)**

<table><thead><tr><th width="228.6614990234375">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Total Return</strong></td><td>Total % gain over the backtest window, plus the dollar value of the final balance.</td></tr><tr><td><strong>Max Drawdown</strong></td><td>The worst peak-to-trough drop in equity — your best gauge of "how much pain to sit through."</td></tr><tr><td><strong>Win Rate</strong></td><td>Share of closed trades that were profitable.</td></tr><tr><td><strong>Profit Factor</strong></td><td>Gross profit ÷ gross loss. >1 means winners outweigh losers; higher is better.</td></tr><tr><td><strong>Sharpe Ratio</strong></td><td>Risk-adjusted return: return per unit of volatility. >1 is decent, >2 is strong.</td></tr></tbody></table>

**Equity curve**

Your equity over time (solid line) vs. **buy-and-hold of the same asset** (dashed line). The gap is whether the strategy added value beyond simply holding the coin.

<figure><img src="../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

**Performance analysis**

<figure><img src="../../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

A deeper breakdown of profit and risk:

<table><thead><tr><th width="304.67706298828125">Metric</th><th>Meaning</th></tr></thead><tbody><tr><td><strong>Total Return vs Buy &#x26; Hold</strong></td><td>Your return next to holding the asset over the same window.</td></tr><tr><td><strong>Outperformance</strong></td><td>How much you beat (or trailed) buy-and-hold.</td></tr><tr><td><strong>Expected payoff</strong></td><td>Average profit per closed trade (net).</td></tr><tr><td><strong>Long vs Short breakdown</strong></td><td>Return % and profit factor for each side separately.</td></tr><tr><td><strong>Sortino</strong></td><td>Like Sharpe, but only penalizes <em>downside</em> volatility.</td></tr><tr><td><strong>Calmar</strong></td><td>CAGR ÷ |Max Drawdown| — return per unit of worst-case pain.</td></tr></tbody></table>

**Trade analysis**

<figure><img src="../../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

An overview of trading activity:

| Metric                            | Meaning                                                                                              |
| --------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Total trades**                  | Number of trades, with a win/loss bar. Your sample size — bigger is more trustworthy.                |
| **Win rate**                      | Share of profitable trades.                                                                          |
| **Largest win / Largest loss**    | Biggest single winner and loser.                                                                     |
| **Avg profit / Avg loss**         | Average gain on winners / average loss on losers.                                                    |
| **Profit factor**                 | Gross profit ÷ gross loss.                                                                           |
| **Avg holding period**            | Average number of bars a position is held (a "bar" = one timeframe interval; on 4h, 6 bars ≈ 1 day). |
| **Max consecutive wins / losses** | Longest winning and losing streaks — a feel for the strategy's streakiness.                          |

> A high win rate with small average wins, or a low win rate with big average wins, can both be healthy — read win rate and profit factor _together_, not alone.

**Trades tab: the trade log**

Every trade executed in the backtest:

| Column                 | Description                                                             |
| ---------------------- | ----------------------------------------------------------------------- |
| **#**                  | Trade number.                                                           |
| **Side**               | LONG or SHORT.                                                          |
| **Entry / Exit Time**  | When the position opened and closed.                                    |
| **Signal**             | What triggered the exit (e.g. `STOP_LOSS`, `TAKE_PROFIT`, `REVERSAL`).  |
| **Entry / Exit Price** | Fill prices.                                                            |
| **P\&L %**             | Profit or loss on that trade.                                           |
| **MAE**                | Maximum Adverse Excursion — worst unrealized drawdown during the trade. |
| **MFE**                | Maximum Favorable Excursion — best unrealized gain during the trade.    |
| **Cumulative P\&L**    | Running total after this trade.                                         |

You can **select specific trades and send them to AI** as context — e.g. _"Why did these get stopped out so early?"_ or _"These shouldn't have exited here — adjust the exit logic."_

<figure><img src="../../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

#### AI Auto-Optimization

After the first backtest, AI can **automatically optimize** toward a better result:

* It runs up to **5 optimization rounds**, trying different approaches while respecting your core requirements.
* If 5 rounds aren't enough, it stops and reports what it tried, why it fell short, and suggested new directions — you can pick one or describe your own.

You can also optimize manually at any time by chatting: _"Reduce the drawdown," "Make it trade more often," "Add a volume filter," "Improve the risk:reward ratio.",_ or click the "Optimize" button.

<figure><img src="../../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

#### Step 4. Live Trading

Once the backtest satisfies you:

1. Click **Run** on the top bar.
2. Select your trading wallet. (Make sure it's idle (not running another strategy).)
3. Review the risk disclosure.
4. Confirm: the strategy deploys and starts running.

**Before going live:** review the disclosure (past performance ≠ future results), confirm the wallet has funds, and make sure you understand the logic (ask AI to explain it anytime).

Alternatively, **Paper trade** to run against live data with no real money: recommended if you want to test the forward run.

**Managing a live strategy:** monitor it in the Autopilot dashboard: account equity, open positions (real-time), recent trades, and a **Stop** button (keep or close positions on stop).

***

### FAQ

**Is the AI a black box?**\
No. Open the Code view: the strategy is plain, editable code with visible entry/exit logic and indicator parameters. AI does the assembly; you can read and change everything.

**What can I control vs. what does the platform control?**\
You define entry signals, exit signals (take-profit, stop-loss, trailing stop, signal reversal), and position actions (open, add, reduce, close). The platform provide supported pairs and caps leverage to levels that passed backtesting without liquidation.

**Is the backtest realistic?**\
Returns are after fees, with slippage as a configurable per-fill cost. However, real fills, partial fills, and capacity still won't match a backtest exactly.

**Will publishing leak my strategy?**\
No, unless you open-sourced your strategy.Strategies are published with a **read-only** backtest report  . Viewers can't see your code or change your code.

**What data feeds the backtests?**\
FMP for TradFi (US stocks, metals, etc.), Binance Futures for crypto.&#x20;

**The platform trade RWA tradfi perps, why backtest on FMP data instead?**\
The tokenized (RWA) contracts on Hyperliquid are still young and don't have enough price history for a trustworthy backtest. Quant validation needs _long_ history to avoid short-term overfitting, so we deliberately use FMP, which provides decades of stock data. The trade-off: Hyperliquid's actual price, order flow, and liquidity will differ from the FMP series. So please treat the backtest as directional evidence, not a promise, and mind the risk when you go live.

**Can I keep improving a strategy after it's live?**\
Yes. Edits create a new version, so the running strategy is untouched. Backtest the new version, stop the live one, and click **Update** to deploy it.

