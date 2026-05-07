# Vibe Trading

Vibe Trading is the natural-language entry point to [Strategy Studio](strategy-studio.md). You describe what you want a strategy to do, and Minara writes the Pine Runtime code, runs a backtest, and deploys it — no manual coding required.

It is not a separate product. The workflow is identical to Strategy Studio: the difference is how you create the strategy. Instead of writing code, you describe your idea in plain language.

{% embed url="https://drive.google.com/file/d/1JlGUdubEmJFT_wHuA0VBYdY1puiYc_lt/view?usp=sharing" %}

## How to use it

**1. Describe your strategy**

In the chat input on the Strategy Studio page, describe your trading logic in plain language. For example:

> "Go long BTC on the 1-hour chart when the 9-EMA crosses above the 21-EMA. Exit when RSI exceeds 70 or when price drops 3% from entry. Use a 5% stop-loss."

Be specific about: the asset, timeframe, entry condition, exit condition, and risk parameters. The more precise your description, the closer the generated code will be to your intent.

**2. Review the generated code**

Minara generates Pine Runtime code and opens it in the Strategy Studio editor. Check the **Code** tab to confirm the logic matches what you described. You can ask Minara to adjust any part of it.

**3. Run the backtest**

Click **Run Backtest** to test the strategy against historical data. Review the results in the **Metrics** tab — total return, drawdown, win rate, profit factor, Sharpe ratio.

**4. Deploy**

When the backtest results are acceptable, deploy the strategy. It runs automatically under the same execution framework as Autopilot.

For full details on backtesting, deployment, and monitoring, see [Strategy Studio](strategy-studio.md).
