# Optimize parameters

## Introduction

The Optimize tab runs a parameter sweep. You pick the values to vary, such as a moving-average length or an RSI threshold, and the tool backtests across the range to show which settings performed best.

{% embed url="https://www.youtube.com/watch?index=5&list=PLUp1UC8-DLnM&v=woSAt79N2Co" %}

## How to use it well

Use it to refine a working strategy, not to manufacture one. A setting that looks best on one historical period often fails on the next, so treat the top result as a starting point and confirm it in Paper rather than deploying it directly.

{% hint style="warning" %}
Tuning a strategy until the backtest looks perfect is overfitting. The more settings you sweep, the more likely the best result is luck. Always confirm an optimized strategy in paper.
{% endhint %}
