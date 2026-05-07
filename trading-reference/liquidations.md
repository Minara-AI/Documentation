# Liquidations

Liquidation happens when your account equity falls below the maintenance margin required to hold a position. The system closes the position to prevent your balance from going negative.

## How liquidation works

Each open position has a **liquidation price** — the asset price at which your margin is insufficient. This price is displayed on every open position in the positions panel. As the market moves against you, your margin ratio decreases. When it reaches the maintenance margin threshold, liquidation is triggered.

The position is closed by Hyperliquid's liquidation engine, typically at or near the liquidation price. Any remaining margin after the close is returned to your account. If the position size is large relative to available liquidity, there may be slippage.

## Auto-deleveraging

In extreme market conditions — sharp moves with insufficient liquidity to fill liquidation orders — Hyperliquid's auto-deleveraging (ADL) system may activate. ADL matches the liquidated position against profitable traders on the opposite side, closing their positions at the bankruptcy price. If your position is selected for ADL, you receive notification and your position is reduced or closed.

ADL is rare and is a last-resort mechanism. It does not incur additional fees.

## How to avoid liquidation

**Set a stop-loss**: place a stop trigger order below (for longs) or above (for shorts) your entry price. This exits the position before it reaches the liquidation price. See [Order types](order-types.md) for how stop triggers work.

**Use lower leverage**: higher leverage brings the liquidation price closer to your entry. At 2x leverage, the asset must drop 50% before liquidation. At 20x, it only needs to drop 5%.

**Monitor your margin ratio**: the positions panel shows your current margin ratio per position. Watch it during volatile periods.

**Use Autopilot's AI Stop-loss**: when running Autopilot, enable the AI Stop-loss feature. It adjusts the stop dynamically based on market conditions and exits positions before they approach the liquidation price.

{% hint style="info" %}
You cannot recover a liquidated position — once triggered, it's closed. The best approach is prevention: lower leverage and a stop-loss set at your maximum acceptable loss.
{% endhint %}
