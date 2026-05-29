# Trading Fees

Your total fee on each trade is the sum of two parts: an exchange fee charged by the perpetuals venue that fills the order (Lighter or Hyperliquid), and a Minara fee charged by the platform. Add the two to get what you pay. What you owe depends on the trading mode you use, the venue, and the asset class.

Each cell shows the fee as `maker / taker`. A maker order adds liquidity (usually a limit order that does not fill immediately). A taker order removes liquidity (a market order, or a limit order that matches a resting order on entry).

## Autopilot & Strategy Studio

**Minara fee:** 0.015% / 0.015% (maker / taker)

| Venue | Asset class | Exchange fee (maker / taker) |
| --- | --- | --- |
| Hyperliquid | Crypto | 0.015% / 0.045% |
| Hyperliquid | Commodities & stocks | 0.003% / 0.009% |
| Lighter | All assets | 0.005% / 0.005% |

Lighter charges one flat rate across every asset it supports. Commodities and stocks cover silver, crude oil, gold, and tokenized US equities. Autopilot does not support prediction markets.

## Copilot & Manual

**Minara fee:** 0.04% / 0.03% (maker / taker)

| Venue | Asset class | Exchange fee (maker / taker) |
| --- | --- | --- |
| Hyperliquid | Crypto | 0.015% / 0.045% |
| Hyperliquid | Commodities & stocks | 0.003% / 0.009% |
| Hyperliquid | Prediction markets | 0.04% / 0.056% |
| Lighter | All assets | 0.005% / 0.005% |

Lighter charges one flat rate across every asset it supports. Commodities and stocks cover silver, crude oil, gold, and tokenized US equities. Prediction markets cover binary outcome contracts on Hyperliquid's Outcome market, powered by Outcomexyz.
