# Run a backtest

## Introduction

A backtest runs your strategy against historical market data and reports how it would have performed. It is the first check on whether an idea holds up before any capital is at risk.

{% embed url="https://www.youtube.com/watch?index=3&list=PLUp1UC8-DLnM&v=nR5dXHPPX1g" %}

## How to run it

1. Open the Code tab.
2. Set the date range and the asset.
3. Click Run Backtest.
4. Read the results in the Metrics tab, with an equity curve and a performance summary.

Backtests cover perpetuals available on Lighter and Hyperliquid, including BTC, ETH, SOL, gold (XAU), silver, and stock perpetuals such as AAPL, TSLA, and NVDA.

## What shapes the numbers

The simulation includes trading fees, slippage, and funding costs for perpetuals, and it sizes positions using the leverage defined by the strategy. Live results can still differ because of available liquidity, order latency, rejected orders, and differences in balance or leverage. Match the timeframe, capital, leverage, and other settings before comparing a live run with its backtest.

{% hint style="warning" %}
A strong backtest does not guarantee live performance. Cold-start bias and overfitting are common, especially over short periods. Validate in the Paper tab before deploying real capital.
{% endhint %}
