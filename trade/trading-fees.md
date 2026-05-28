# Trading Fees

Your total fee on each trade is the sum of two components: an exchange fee charged by the underlying perpetuals venue (Lighter or Hyperliquid), and a Minara fee charged by the platform. Fees vary by venue, asset class, and trading mode.

A maker order adds liquidity to the order book, typically a limit order that does not fill immediately. A taker order removes liquidity, such as a market order or a limit order that matches an existing order on entry.

## Hyperliquid

**Maker fees**

| Asset class | Mode | Hyperliquid fee | Minara fee | Total |
| --- | --- | --- | --- | --- |
| Crypto | Autopilot | 0.015% | 0.015% | **0.03%** |
| Crypto | Copilot | 0.015% | 0.04% | **0.065%** |
| Commodities & stocks | Autopilot | 0.003% | 0.015% | **0.018%** |
| Commodities & stocks | Copilot | 0.003% | 0.04% | **0.043%** |
| Prediction markets | Copilot | 0.04% | 0.04% | **0.08%** |

**Taker fees**

| Asset class | Mode | Hyperliquid fee | Minara fee | Total |
| --- | --- | --- | --- | --- |
| Crypto | Autopilot | 0.045% | 0.015% | **0.06%** |
| Crypto | Copilot | 0.045% | 0.03% | **0.075%** |
| Commodities & stocks | Autopilot | 0.009% | 0.015% | **0.024%** |
| Commodities & stocks | Copilot | 0.009% | 0.03% | **0.039%** |
| Prediction markets | Copilot | 0.056% | 0.03% | **0.086%** |

Commodities and stocks share one fee tier and cover silver, crude oil, gold, and tokenized US equities. Prediction markets cover binary outcome contracts traded on Hyperliquid's Outcome market, powered by Outcomexyz.

## Lighter

Lighter uses a flat fee schedule across all supported assets; there is no per-asset-class differentiation.

**Maker fees**

| Mode | Lighter fee | Minara fee | Total |
| --- | --- | --- | --- |
| Autopilot | 0.005% | 0.015% | **0.020%** |
| Copilot | 0.005% | 0.030% | **0.035%** |

**Taker fees**

| Mode | Lighter fee | Minara fee | Total |
| --- | --- | --- | --- |
| Autopilot | 0.005% | 0.015% | **0.020%** |
| Copilot | 0.005% | 0.040% | **0.045%** |
