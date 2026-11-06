# Optimize the factor mix

Optimize asks Minara to tune a cross-sectional strategy for you. It tests variations of the factor mix and the ranking settings, then reports which performed best.

{% embed url="https://www.youtube.com/watch?index=11&list=PLUp1UC8-DLnM&v=iZpSz-WaZR0" %}

## What it varies

| Lever                 | What Minara tries                        |
| --------------------- | ---------------------------------------- |
| Factor weights        | Shifting how much each factor counts     |
| Factor set            | Adding or dropping factors from the mix  |
| Long and short counts | Holding more or fewer names on each side |
| Rebalance             | Testing different rebalance frequencies  |

## How to use it

1. Open a cross-sectional strategy with a backtest already run.
2. Click Optimize.
3. Minara runs several rounds, each testing a variation, and ranks them by the target metric.
4. Review the results. If a variation beats your current mix, apply it; if none do, the original settings are kept.

{% hint style="warning" %}
Optimizing on one period can fit the past rather than find a real edge. Prefer a mix that holds up across the full window and in paper trading over one that only wins the optimization.
{% endhint %}
