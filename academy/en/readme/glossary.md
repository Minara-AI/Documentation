# Glossary

Plain-language definitions of the terms used across this guide, grouped by topic.

{% embed url="https://www.youtube.com/watch?index=1&list=PLUp1UC8-DLnM&v=aVq7ZEBihB4" %}

**Strategy types**

* **Time-series strategy** — trades one asset by reacting to signals on its own price over time, deciding when to go long, short, or flat.
* **Cross-sectional strategy** — trades a basket of assets by scoring and ranking them against each other, holding the top and shorting the bottom.
* **Long** — a position that profits when the price goes up.
* **Short** — a position that profits when the price goes down.
* **Signal** — a condition on price or data that tells the strategy to enter or exit.
* **Rebalance** — recomputing the ranking on a schedule and adjusting the portfolio to match.

**Universe and factors**

* **Universe** — the fixed pool of assets a cross-sectional strategy ranks and picks from, such as TradFi 30, Coin 30, or Coin 50.
* **Factor** — a rule that turns each asset into a comparable score, such as 5-day return or a normalized MACD.
* **Ranking** — ordering every asset in the universe by its factor score to decide what to hold.
* **Z-score** — a factor value expressed as how many standard deviations it sits from the universe average, so different factors can be combined on one scale.
* **Equal-weighted** — giving every holding (or every factor) the same weight rather than sizing by conviction.

**Price signals and indicators**

* **Moving average (MA)** — the average price over a set number of bars, used to smooth out noise and define trend.
* **EMA** — an exponential moving average that weights recent prices more heavily than older ones.
* **RSI** — the Relative Strength Index, a 0–100 gauge of how overbought or oversold an asset is.
* **MACD** — the difference between two EMAs, used to read momentum shifts against its own signal line.
* **Breakout** — a move where price pushes above a recent high or below a recent low, often used as an entry.
* **Bollinger Bands** — a moving-average band that widens and narrows with volatility, marking stretched prices.
* **Momentum** — the tendency of recent winners to keep outperforming over the near term.
* **Mean reversion** — the tendency of stretched prices to move back toward their average.
* **Volatility** — how much an asset's price swings, higher meaning larger and more frequent moves.

**Backtesting**

* **Backtest** — running a strategy against historical data to see how it would have performed.
* **Paper trading** — running a strategy live against real prices with no real capital, to validate it before deploying.
* **Equity curve** — the line showing how the account balance would have grown or shrunk over the backtest.
* **Fill** — a single executed trade; total fills counts every entry and exit, including rebalances.
* **Overfitting** — tuning a strategy so tightly to past data that it captures noise and fails on new data.
* **Cold-start bias** — misleading results from a backtest window too short or too favorable to be representative.

**Sizing and execution**

* **Leverage** — a multiplier that turns a slice of your capital into a larger market position, magnifying both gains and losses.
* **Margin** — the share of your equity set aside as collateral for a leveraged position.
* **Perpetual (perp)** — a futures contract with no expiry, the instrument Strategy Studio trades on Lighter and Hyperliquid.
* **Notional** — the full market value of a position, equal to margin times leverage.
* **Commission** — the exchange fee paid on each trade. Minara includes trading fees in both backtest engines so reported results already reflect this cost.

**Return metrics**

* **Total Return** — the overall percentage gain or loss across the whole backtest period.
* **CAGR** — the compound annual growth rate, the return restated as a steady yearly rate.
* **Profit Factor** — gross profit divided by gross loss, where above 1.0 means the strategy made money.
* **Win Rate** — the share of trades that closed in profit.
* **Win/loss ratio** — the average winning trade divided by the average losing trade.
* **Expected payoff** — the average profit or loss per trade across all trades.

**Risk metrics**

* **Max Drawdown** — the largest drop from a peak to the following trough, showing the worst stretch to sit through.
* **Sharpe Ratio** — return per unit of total risk, where above 1.0 is acceptable and above 2.0 is strong.
* **Sortino Ratio** — like Sharpe but penalizing only downside volatility, rewarding strategies whose big moves are upward.
* **Calmar Ratio** — CAGR divided by max drawdown, measuring return against worst-case pain.
* **Alpha** — return earned beyond what the benchmark explains.
* **Beta** — how strongly the strategy moves with its benchmark, where 1.0 tracks it one-for-one.

**Cross-sectional metrics**

* **Information Coefficient (IC)** — how well a factor's ranking lined up with the returns that followed, higher and steadier being better.
* **Quantile returns** — the return of each ranked group of the universe, which should line up in order when a factor works.
* **Turnover** — how much the portfolio changes at each rebalance, where high turnover raises live trading costs.

**Portfolio and exposure**

* **Long exposure** — the total size of long positions as a share of capital.
* **Short exposure** — the total size of short positions as a share of capital.
* **Net exposure** — long exposure minus short exposure, showing the overall directional tilt.
* **Composition** — the breakdown of trading volume or holdings across the symbols a strategy traded.
* **Avg holding period** — how long a position is held on average before it closes.

**Going live**

* **Deploy** — locking a strategy's current version into a running instance so it can trade.
* **Autopilot** — the mode that runs a deployed strategy on its own, opening and closing positions without manual input.
* **APY** — the annualized yield of a deployed strategy, based on realized profit since deployment.
