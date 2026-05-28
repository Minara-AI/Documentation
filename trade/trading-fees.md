# Trading Fees

Your total fee on each trade is the sum of two components: an exchange fee charged by the underlying perpetuals venue (Lighter or Hyperliquid), and a Minara fee charged by the platform. Fees vary by venue, asset class, and trading mode.

A maker order adds liquidity to the order book, typically a limit order that does not fill immediately. A taker order removes liquidity, such as a market order or a limit order that matches an existing order on entry.

## Hyperliquid

### Autopilot

| Asset class | Hyperliquid maker | Minara maker | Maker total | Hyperliquid taker | Minara taker | Taker total |
| --- | --- | --- | --- | --- | --- | --- |
| Crypto | 0.015% | 0.015% | **0.03%** | 0.045% | 0.015% | **0.06%** |
| Commodities & stocks | 0.003% | 0.015% | **0.018%** | 0.009% | 0.015% | **0.024%** |

### Copilot

| Asset class | Hyperliquid maker | Minara maker | Maker total | Hyperliquid taker | Minara taker | Taker total |
| --- | --- | --- | --- | --- | --- | --- |
| Crypto | 0.015% | 0.04% | **0.065%** | 0.045% | 0.03% | **0.075%** |
| Commodities & stocks | 0.003% | 0.04% | **0.043%** | 0.009% | 0.03% | **0.039%** |
| Prediction markets | 0.04% | 0.04% | **0.08%** | 0.056% | 0.03% | **0.086%** |

Commodities and stocks share one fee tier and cover silver, crude oil, gold, and tokenized US equities. Prediction markets cover binary outcome contracts traded on Hyperliquid's Outcome market, powered by Outcomexyz; Autopilot does not support prediction markets.

## Lighter

Lighter uses a flat fee schedule across all supported assets; there is no per-asset-class differentiation.

### Autopilot

| | Maker | Taker |
| --- | --- | --- |
| Lighter fee | 0.005% | 0.005% |
| Minara fee | 0.015% | 0.015% |
| **Total** | **0.020%** | **0.020%** |

### Copilot

| | Maker | Taker |
| --- | --- | --- |
| Lighter fee | 0.005% | 0.005% |
| Minara fee | 0.030% | 0.040% |
| **Total** | **0.035%** | **0.045%** |
