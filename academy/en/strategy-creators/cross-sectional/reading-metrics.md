# Reading the metrics

A cross-sectional backtest reports the same portfolio metrics as a time-series one, such as return, drawdown, and Sharpe, plus a few that are specific to ranking strategies. Read them together rather than one at a time.

{% embed url="https://www.youtube.com/watch?index=9&list=PLUp1UC8-DLnM&v=drhaS1Yhfvk" %}

## Return, drawdown, and Sharpe

These describe the long/short portfolio as a whole, the same way they do for a time-series strategy. Total return and max drawdown show the size of the gains and the worst loss along the way. Sharpe puts the return against its volatility.

## IC

The information coefficient measures how well the factor ranking lined up with the returns that followed, across the whole universe. A higher, steadier IC means the ranking carried real information rather than noise. A high average IC that swings between positive and negative is less reliable than a lower, steadier one.

## Quantile returns

Quantile returns split the universe into ranked groups and show the return of each. In a ranking that works, the top group outperforms the bottom group and the groups line up in order. If the middle groups beat the top, the factor is not ranking cleanly.

## Turnover

Turnover measures how much the portfolio changes at each rebalance. High turnover means the ranking reshuffles often, which raises trading costs in live trading. A strategy that looks good before costs can weaken once turnover is paid for.

## Reading them together

A healthy cross-sectional backtest usually shows a steady IC, quantile returns that line up in rank order, a positive Sharpe, and turnover low enough that costs do not erase the edge. If the IC is high but quantiles are jumbled, or returns are strong but turnover is very high, treat the result with caution.
