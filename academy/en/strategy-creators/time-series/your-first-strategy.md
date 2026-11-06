# Your first time-series strategy

A time-series strategy trades one asset by reacting to signals on its own price. Here is the full path from an idea to a deployed strategy.&#x20;

→ [https://minara.ai/app/strategy-studio](https://minara.ai/app/strategy-studio)&#x20;

{% embed url="https://www.youtube.com/watch?index=2&list=PLUp1UC8-DLnM&v=uuf1esO-smw" %}

## Describe the idea

Click New Strategy, keep the toggle on Time-series, and describe your idea in the prompt box. Minara writes the code from your description, so be specific about four things: the asset, the timeframe, the entry condition, and the exit condition.

> Go long BTC on the 1-hour chart when the 9-EMA crosses above the 21-EMA. Exit when RSI exceeds 70 or price drops 3% from entry.

A few more to start from:

> Short ETH on the 15-minute chart when MACD crosses below signal and price is below the 200-EMA.

> Long NVDA perpetual on the 4-hour chart when price breaks above the 20-day high on above-average volume.

## Check what Minara generated

Open the Code tab and read the strategy Minara wrote, to confirm the entry and exit conditions are the ones you meant. If something is off, ask for the change in chat and Minara updates the code. You refine through chat rather than editing code by hand.

## Backtest it

Set the asset and the date range, then click Run Backtest. Minara runs the strategy against your price history and fills in the metrics, with an equity curve and a performance summary. Open Metrics to read the results and Trades to see each entry and exit.

## Paper trade, then deploy

Run it in the Paper tab to watch it trade against live prices with no real capital. When the results hold up, click Deploy to put it live.

{% hint style="info" %}
Generated code is a starting point. Read it before backtesting, and validate in paper trading before you deploy real capital.
{% endhint %}

The rest of this track explains each step in more detail: running a backtest, reading the metrics, and optimizing the parameters.
