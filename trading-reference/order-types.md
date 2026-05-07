# Order types

Minara's trading panel supports two primary order types, with modifiers that change how they execute. The same order types are available for crypto, stocks, and commodities.

## Market order

A market order executes immediately at the best available price on the order book. You get filled quickly, but the exact price depends on current liquidity.

Use a market order when speed of execution matters more than price precision — for example, closing a position quickly during volatile conditions.

## Trigger order

A trigger order waits until the asset reaches a price you specify, then executes. There are two sub-types:

**Limit trigger**: when the trigger price is reached, the order is placed as a limit order at your specified price. You will be filled at that price or better, but the order may not fill at all if the market moves away.

**Stop trigger**: when the asset crosses a threshold price, the order executes at market. Used for stop-losses — it guarantees an exit but not a specific price.

## Order modifiers

**Reduce Only**: the order will only reduce an existing position, never increase it or open a new one. Useful when placing stop-loss or take-profit orders to ensure they don't accidentally flip your position.

**Post Only**: the order will only be placed as a maker order (added to the order book). If it would execute immediately as a taker, it is cancelled instead. Use this to avoid taker fees.

## Take-profit and stop-loss (TP/SL)

You can attach take-profit and stop-loss levels to an open position directly from the positions panel. These are stored as conditional trigger orders that activate when the price reaches your target.

- **Take-profit**: closes the position (fully or partially) when price moves in your favor to the target level
- **Stop-loss**: closes the position when price moves against you to the threshold level

{% hint style="info" %}
Autopilot and Strategy Studio manage TP/SL automatically. When trading manually via Copilot, Minara's signal cards suggest TP and SL levels — you set them yourself when placing the order.
{% endhint %}
