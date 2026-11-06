# Reading the backtest metrics

The Metrics tab summarizes how the strategy performed. Each number answers a different question, and reading them together tells you more than any single one. This page explains the headline metrics, then how to weigh them against each other.&#x20;

{% embed url="https://www.youtube.com/watch?index=4&list=PLUp1UC8-DLnM&v=3cnCBwW43PY" %}

## The metrics at a glance

| Metric        | What it measures                                 | A rough read                                  |
| ------------- | ------------------------------------------------ | --------------------------------------------- |
| Total Return  | Gain or loss over the whole backtest period      | Higher is better, but read it with drawdown   |
| Max Drawdown  | Largest drop from a peak to the following trough | Lower is better; set a limit you can tolerate |
| Win Rate      | Share of trades that closed in profit            | Read together with profit factor, not alone   |
| Profit Factor | Gross profit divided by gross loss               | Above 1.0 made money; 1.1 to 1.3 is common    |
| Sharpe Ratio  | Return per unit of total risk                    | Above 1.0 is acceptable, above 2.0 is strong  |
| Sortino Ratio | Return per unit of downside risk                 | Higher means losses are well contained        |

## Return and drawdown

Total Return is the headline, but it hides the path the strategy took to get there. A strategy can double an account and still be unusable if it nearly blew up along the way, which is what Max Drawdown captures.

* A drawdown of 20% means the account fell one fifth from its high point before recovering.
* Most traders set a drawdown they can tolerate and discard strategies that breach it, whatever the total return.

Read the two together. High return with a deep drawdown is a strategy you may not be able to hold through its worst stretch.

## Win rate and profit factor

Win Rate on its own can mislead.

* A strategy that wins 30% of the time can still be profitable if its winners are much larger than its losers.
* A strategy that wins 80% of the time can lose money if its rare losses are large.

Read Win Rate together with Profit Factor. A Profit Factor above 1.0 means the strategy made money overall, and the further above 1.0, the more cushion it has. Values around 1.1 to 1.3 are common for workable strategies. A much higher number on a short backtest is a reason to check for overfitting, not a reason to trust it.

## Sharpe and Sortino

Both ratios measure return against risk, which is what lets you compare two strategies with different return levels.

* Sharpe penalizes all volatility, including upside swings.
* Sortino penalizes only downside volatility, so it rewards a strategy whose large moves are mostly in your favor.

A Sharpe above 1.0 is generally acceptable and above 2.0 is strong, though short backtests inflate these numbers.

## Reading them together

No single metric tells you whether a strategy is sound. Check them as a set:

* Return is positive and came from a reasonable number of trades, not one lucky move.
* Max Drawdown stays inside a level you can hold through.
* Profit Factor is comfortably above 1.0, and Win Rate and Profit Factor make sense together.
* Sharpe and Sortino hold up, and are not inflated by a short test window.

If all four hold, the strategy is worth validating in paper. If any one breaks, fix the strategy before moving on.
