# Crypto perpetuals

Minara trades crypto perpetuals on Hyperliquid — a high-performance on-chain order book. Perpetuals are futures contracts with no expiry date. You hold them as long as you want, and the contract price tracks the underlying asset via a funding rate mechanism.

## Supported assets

All assets available on Hyperliquid are available in Minara, including BTC, ETH, SOL, and many others. The full list appears in the asset selector at `/app/trade/perps`.

## How perpetuals work

**No expiry**: unlike traditional futures, perpetuals don't settle on a fixed date. You open a position and hold it indefinitely, or until you close it or get liquidated.

**Funding rates**: to keep the perpetual price close to the spot price, a funding payment is exchanged between long and short holders periodically. When funding is positive, longs pay shorts; when negative, shorts pay longs. The current funding rate is shown in the trading interface.

**Leverage**: Minara supports up to 25x leverage on crypto perpetuals. Leverage multiplies both gains and losses. See [Margin and leverage](margin-and-leverage.md) for how margin requirements work.

## The trading interface

The trading panel is on the right side of the screen. Two order types are available:

- **Market**: executes immediately at the best available price
- **Trigger**: executes when the asset reaches a price you specify

Both Autopilot and Copilot use this same underlying interface. If you're using Copilot, the AI generates a signal card with suggested entry, take-profit, and stop-loss levels — you place the order manually.

{% hint style="info" %}
Minara routes orders through Hyperliquid's on-chain order book. Execution is non-custodial: your funds stay in your Hyperliquid account, not held by Minara.
{% endhint %}

## Fees

Trading fees apply to all perpetual trades. See [Trading fees](../guide/managing-funds-and-trading/trading-fees.md) for the current rate schedule.
