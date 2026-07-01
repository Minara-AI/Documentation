---
hidden: true
---

# Copy of Create Time-series Strategies

## Left sidebar

The sidebar shows two sections:

* **Deployed**: strategies currently running live. Each deployed strategy shows its live APY and the asset it trades.
* **Drafts**: strategies you're editing or have not yet deployed. Changes to a draft never affect a deployed strategy.

Click any entry to open it in the editor.

## Create a new strategy

Click **New Strategy** in the top-right corner. Two options:

* **Describe your idea in chat**: type what you want the strategy to do in plain language. Minara generates the Pine Runtime code. This is what Minara calls "Vibe Trading": you describe the logic, the AI writes the code.
* **Write code directly**: start from a blank editor or an existing template and write Pine Runtime yourself.

Either way, the strategy opens in draft state. Nothing runs until you deploy.

### Creating from a description

Be specific about four things: asset, timeframe, entry condition, exit condition. For example:

> "Go long BTC on the 1-hour chart when the 9-EMA crosses above the 21-EMA. Exit when RSI exceeds 70 or price drops 3% from entry."

Other examples to get started:

> "Short ETH on the 15-minute chart when MACD crosses below signal and price is below the 200-EMA."

> "Go long SOL when the daily RSI crosses above 40 coming from oversold. Exit at 10% gain or 5% loss."

> "Long NVDA perpetual on the 4-hour chart when price breaks above the 20-day high with above-average volume."

After Minara generates the code, open the **Code** tab to verify the logic matches your intent. Ask follow-up questions to adjust any part of it before running a backtest.

## Editor tabs

| Tab      | What it shows                                     |
| -------- | ------------------------------------------------- |
| Code     | Pine Runtime source code for your strategy        |
| Metrics  | Backtest performance summary                      |
| Trades   | Individual trade log from the backtest            |
| Paper    | Live paper trading (no real capital)              |
| Optimize | Parameter sweep tool for finding optimal settings |

## Run a backtest

In the **Code** tab, set your date range and asset, then click **Run Backtest**. Results appear in the **Metrics** tab.

Backtests are supported for perpetual assets available on Lighter and Hyperliquid, including Bitcoin (BTC), Ethereum (ETH), Solana (SOL), gold (XAU), silver, and stock perpetuals such as Apple (AAPL), Tesla (TSLA), and NVIDIA (NVDA).

### What each metric means

| Metric        | What it tells you                                                           |
| ------------- | --------------------------------------------------------------------------- |
| Total Return  | Percentage gain or loss over the backtest period                            |
| Max Drawdown  | Largest peak-to-trough decline; measures worst-case loss                    |
| Win Rate      | Percentage of trades that closed in profit                                  |
| Profit Factor | Gross profit divided by gross loss; above 1.0 means the strategy made money |
| Sharpe Ratio  | Return per unit of risk; above 1.0 is generally acceptable                  |
| Sortino Ratio | Like Sharpe but only penalizes downside volatility                          |

{% hint style="info" %}
A strong backtest does not guarantee live performance. Cold-start bias and overfitting are common. Use the **Paper** tab to validate the strategy in live conditions before deploying real capital.
{% endhint %}

## Deploy a strategy

When you're satisfied with the backtest and paper results, click **Deploy**. This locks the current version of your code into a running strategy. The deployed strategy appears under **Deployed** in the sidebar with a live APY counter.

Two things to know:

1. **Editing a draft does not affect the live strategy.** The deployed version runs the code that was current at deployment time. To update a live strategy, you must deploy again.
2. **You cannot stop a deployed strategy without closing its positions.** Stopping it closes all open positions it manages.

## Monitor a deployed strategy

Click a deployed strategy to view:

* **APY**: annualized return since deployment
* **Positions**: current open positions and their unrealized P\&L
* **Trade log**: every entry and exit, with timestamps and realized P\&L

{% hint style="info" %}
APY is calculated from the strategy's realized P\&L since deployment. It resets if you stop and redeploy the strategy.
{% endhint %}
