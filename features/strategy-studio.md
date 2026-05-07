# Strategy Studio

Strategy Studio is where you build, backtest, and deploy algorithmic trading strategies. Strategies are written in Pine Runtime — Minara's TypeScript DSL — and run against historical market data before going live. A deployed strategy executes automatically, opening and closing positions according to your code.

Find it at `/app/trade/strategy-studio`.

## Left sidebar

The sidebar shows two sections:

- **Deployed**: strategies currently running live. Each deployed strategy shows its live APY and the asset it trades.
- **Drafts**: strategies you're editing or have not yet deployed. Changes to a draft never affect a deployed strategy.

Click any entry to open it in the editor.

## Create a new strategy

Click **New Strategy** in the top-right corner. You have two options:

- **Describe your idea in chat**: type what you want the strategy to do ("Go long BTC when RSI is below 30 and close when it crosses 50"). Minara generates the Pine Runtime code for you.
- **Write code directly**: start from a blank editor or an existing template and write Pine Runtime code yourself.

Either way, the strategy opens in draft state. Nothing runs until you deploy.

## Editor tabs

| Tab | What it shows |
|---|---|
| Code | Pine Runtime source code for your strategy |
| Metrics | Backtest performance summary |
| Trades | Individual trade log from the backtest |
| Paper | Live paper trading (no real capital) |
| Optimize | Parameter sweep tool for finding optimal settings |

## Run a backtest

In the **Code** tab, set your date range and asset, then click **Run Backtest**. Results appear in the **Metrics** tab.

### What each metric means

| Metric | What it tells you |
|---|---|
| Total Return | Percentage gain or loss over the backtest period |
| Max Drawdown | Largest peak-to-trough decline; measures worst-case loss |
| Win Rate | Percentage of trades that closed in profit |
| Profit Factor | Gross profit divided by gross loss; above 1.0 means the strategy made money |
| Sharpe Ratio | Return per unit of risk; higher is better; above 1.0 is generally acceptable |
| Sortino Ratio | Like Sharpe but only penalizes downside volatility |

{% hint style="info" %}
A strong backtest does not guarantee live performance. Cold-start bias and overfitting are common. Use the **Paper** tab to validate the strategy in live market conditions before deploying real capital.
{% endhint %}

## Deploy a strategy

When you're satisfied with the backtest and paper results, click **Deploy**. This locks the current version of your code into a running strategy. The deployed strategy appears under **Deployed** in the sidebar with a live APY counter.

Two things to know about deployment:

1. **Editing a draft does not affect the live strategy.** The deployed version runs the code that was current at deployment time. To update a live strategy, you must deploy again.
2. **You cannot "un-deploy" without closing positions.** Stopping a deployed strategy closes all open positions it manages.

## Monitor a deployed strategy

Click a deployed strategy to view:

- **APY**: annualized return since deployment
- **Positions**: current open positions and their unrealized P&L
- **Trade log**: every entry and exit, with timestamps and realized P&L

{% hint style="info" %}
APY is calculated from the strategy's realized P&L since deployment. It resets if you stop and redeploy the strategy.
{% endhint %}
