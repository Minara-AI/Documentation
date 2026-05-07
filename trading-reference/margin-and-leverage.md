# Margin and leverage

Margin is the collateral you put up to open a leveraged position. Leverage lets you control a larger position than your account balance would otherwise allow, multiplying both potential gains and potential losses.

## Cross-margin

Minara uses cross-margin by default. This means all available USDC in your Hyperliquid account backs your open positions collectively. If one position runs at a loss, the remaining account balance absorbs it before liquidation occurs.

The advantage is that you don't need to allocate funds per position. The risk is that losses on one trade reduce the margin available to all other open positions.

## Leverage limits

| Asset class | Maximum leverage |
|---|---|
| Crypto perpetuals (BTC, ETH, SOL, etc.) | 25x |
| Stocks (AAPL, TSLA, NVDA, AMZN, MSFT) | Lower (varies by asset) |
| Commodities (Gold/XAU, Silver, Crude Oil) | Lower (varies by asset) |

The leverage selector is in the trading panel. Choose a lower multiplier to reduce liquidation risk.

## Initial margin

Initial margin is the USDC required to open a position:

```
Initial margin = (position size × entry price) / leverage
```

For example: opening a $10,000 BTC position at 10x leverage requires $1,000 in initial margin.

## Maintenance margin

Maintenance margin is the minimum equity required to keep a position open. It is lower than initial margin. If your account equity falls below the maintenance margin level for a position, that position is subject to liquidation.

The maintenance margin requirement and your current margin ratio are shown on each open position in the positions panel.

## What happens when margin runs out

If your equity falls below the maintenance margin level, the system closes your position. See [Liquidations](liquidations.md) for the full process, including how to avoid it and what auto-deleveraging means.

{% hint style="info" %}
The simplest way to avoid liquidation is to use lower leverage and set a stop-loss. Autopilot's AI Stop-loss feature exits positions before the liquidation price is reached.
{% endhint %}
