# Time-series strategies

**What is a time-series strategy, and when should I use it?** It trades one asset by reacting to signals on its own price, so it answers timing: when to go long or short. Use it when your idea is about a single chart, such as entering BTC on an EMA cross and exiting on an RSI level.

**What should I describe to generate one?** Be specific about four things: the asset, the timeframe, the entry condition, and the exit condition. For example, go long BTC on the 1-hour chart when the 9-EMA crosses above the 21-EMA, and exit when RSI exceeds 70 or price drops 3% from entry.

**How does a time-series backtest work?** It replays your entry and exit rules against one asset's price history over the date range you set, then reports the equity curve, the metrics, and every trade. Set the asset and range in the Code tab and click Run Backtest.
