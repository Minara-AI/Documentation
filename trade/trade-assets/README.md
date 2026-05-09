# Assets

Minara supports three categories of tradable assets: crypto perpetuals, tokenized stock perpetuals, and commodity perpetuals, all settled in USDC on Hyperliquid's on-chain order book.

***

## Crypto perpetuals

Minara trades crypto perpetuals on Hyperliquid, a high-performance on-chain order book. Perpetuals are futures contracts with no expiry date. You hold them as long as you want, and the contract price tracks the underlying asset via a funding rate mechanism.

**Supported assets**: all assets available on Hyperliquid are available in Minara, including Bitcoin (BTC), Ethereum (ETH), Solana (SOL), and many others. Popular pairs include BTC/USDC, ETH/USDC, and SOL/USDC. You can also trade hundreds of altcoin perpetuals from the same interface. The full list appears in the asset selector at `/app/trade/perps`.

**No expiry**: unlike traditional futures, perpetuals don't settle on a fixed date. You open a position and hold it indefinitely, or until you close it or get liquidated.

**Funding rates**: to keep the perpetual price close to the spot price, a funding payment is exchanged between long and short holders periodically. When funding is positive, longs pay shorts; when negative, shorts pay longs. The current funding rate is shown in the trading interface.

**Leverage**: Minara supports up to 25x leverage on crypto perpetuals. Leverage multiplies both gains and losses. See [Margin and leverage](../../trading-reference/margin-and-leverage.md) for how margin requirements work.

The trading panel is on the right side of the screen. Two order types are available: **Market** (executes immediately at the best available price) and **Trigger** (executes when the asset reaches a price you specify). Both Autopilot and Copilot use this same underlying interface.

{% hint style="info" %}
Minara routes orders through Hyperliquid's on-chain order book. Execution is non-custodial: your funds stay in your Hyperliquid account, not held by Minara.
{% endhint %}

***

## Stocks

Minara gives you access to tokenized stocks as perpetual contracts on Hyperliquid. You can trade Apple (AAPL), Tesla (TSLA), NVIDIA (NVDA), Amazon (AMZN), Microsoft (MSFT), and other major equities using the same USDC-based interface as crypto.

These are perpetual contracts whose price tracks the underlying stock. They are not actual shares. You do not receive dividends, voting rights, or any equity ownership. You are taking a leveraged position on the price movement of the stock. Trading is available 24/7, including outside traditional market hours, though liquidity and spreads may vary when the underlying exchange is closed.

The trading mechanics are identical to crypto perpetuals: positions are denominated in USDC, funding rates apply, leverage is available (at lower maximums than crypto perps), and orders can be placed as market or trigger orders. Filter by **Stocks** in the asset selector to see all available instruments.

{% hint style="info" %}
Because these are perpetuals tracking stock prices rather than direct ownership, your exposure ends when you close the position. There is no settlement or delivery.
{% endhint %}

***

## Commodities

Minara supports trading commodity perpetuals including gold (XAU), silver (SILVER), and crude oil via Hyperliquid's order book.

* **Gold (XAU)**: trade gold perpetuals as XAUUSDC, priced in USDC, 24/7 without a brokerage account.
* **Silver (SILVER)**: silver futures perpetual, priced in USDC.
* **Crude oil**: available as a perpetual contract.

More commodities may be added as Hyperliquid listings expand. Filter by **Commodities** in the asset selector to see the current list.

Commodity perpetuals work the same way as crypto perpetuals: no expiry, funding rates, and leverage available. Commodities are available 24/7, though liquidity varies by session.

{% hint style="info" %}
Commodity perpetuals track the underlying commodity price via oracle feeds. You are not taking delivery of physical goods.
{% endhint %}

***

## Fees

Trading fees apply to all perpetual trades and vary by asset class. See [Trading fees](../trading-fees.md) for the current rate schedule.
