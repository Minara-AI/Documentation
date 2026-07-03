# Trading fees

Your total fee on each trade depends on the trading mode you use, the venue that fills the order (Lighter or Hyperliquid), and the asset class. Each table below shows the final fee you pay.

Each cell shows the fee as `maker / taker`. A maker order adds liquidity (usually a limit order that does not fill immediately). A taker order removes liquidity (a market order, or a limit order that matches a resting order on entry).

{% hint style="info" %}
Some TradFi assets on Hyperliquid, such as GOLD, carry higher fees than the rates shown below. For each asset's real-time trading fee, we recommend checking with Hyperliquid.
{% endhint %}

## Autopilot & Strategy Studio

| Venue       | Asset class                   | maker / taker   |
| ----------- | ----------------------------- | --------------- |
| Hyperliquid | Crypto                        | 0.030% / 0.060% |
| Hyperliquid | TradFi (commodities & stocks) | 0.018% / 0.024% |
| Lighter     | All assets                    | 0.020% / 0.020% |

Lighter charges one flat rate across every asset it supports. Commodities and stocks cover silver, crude oil, and tokenized US equities. Autopilot does not support prediction markets.

## Copilot & Manual

| Venue       | Asset class          | maker / taker   |
| ----------- | -------------------- | --------------- |
| Hyperliquid | Crypto               | 0.055% / 0.075% |
| Hyperliquid | Commodities & stocks | 0.043% / 0.039% |
| Hyperliquid | Prediction markets   | 0.080% / 0.086% |
| Lighter     | All assets           | 0.045% / 0.035% |

Lighter charges one flat rate across every asset it supports. Commodities and stocks cover silver, crude oil, gold, and tokenized US equities. Prediction markets cover binary outcome contracts on Hyperliquid's Outcome market, powered by Outcomexyz.
