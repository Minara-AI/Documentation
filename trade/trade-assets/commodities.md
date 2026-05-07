# Commodities

Minara supports trading commodity perpetuals, including gold (XAU), silver (SILVER), and crude oil, via Hyperliquid's order book.

## Available instruments

* **Gold (XAU)**: trade gold perpetuals as XAUUSDC, priced in USDC. Gold is one of the most liquid commodity markets globally and trades 24/7 on Minara without a brokerage account.
* **SILVER**: silver futures perpetual, priced in USDC
* **Crude oil**: available as a perpetual contract

More commodities may be added as Hyperliquid listings expand. Check the asset selector and filter by **Commodities** to see the current list.

## Trading mechanics

Commodity perpetuals work the same way as crypto perpetuals: no expiry, funding rates, and leverage available. The trading interface is identical — market and trigger orders, with take-profit and stop-loss support.

Commodities are available 24/7, though liquidity varies by session.

## Fees

Hyperliquid charges lower fees for commodity perpetuals than for crypto:

* Maker: 0.003%
* Taker: 0.009%

These apply per trade on the notional position size. Full fee details, including any Minara platform fees, are in [Trading fees](../trading-fees.md).

{% hint style="info" %}
Commodity perpetuals track the underlying commodity price via oracle feeds. As with all perpetuals on Hyperliquid, you are not taking delivery of physical goods.
{% endhint %}
