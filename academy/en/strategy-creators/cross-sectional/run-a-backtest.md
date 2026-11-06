# Run a backtest

A cross-sectional backtest replays your ranking across history. On each rebalance date it scores every asset in the universe, ranks them, holds the top and shorts the bottom, then measures how that portfolio would have performed.

{% embed url="https://www.youtube.com/watch?index=8&list=PLUp1UC8-DLnM&v=higXD-uKQcc" %}

## How to run it

1. Set the universe, the factor mix, the long and short counts, and the rebalance.
2. Set the date range to test over.
3. Click Run Backtest.
4. Read the results in the metrics, with the equity curve and a performance summary.

## What shapes the numbers

A cross-sectional backtest depends on the whole universe having history over the test window. Names with gaps are handled on the rebalance dates, so results can shift if you change the universe or the rebalance schedule. Trading fees, slippage, and funding costs for perpetuals are included in the simulation. Live results can still differ because of available liquidity, order latency, rejected orders, and account settings.

{% hint style="warning" %}
A strong backtest does not guarantee live performance. Factor rankings decay, and a mix tuned on one period can fail on the next. Validate in paper trading before deploying real capital.
{% endhint %}
