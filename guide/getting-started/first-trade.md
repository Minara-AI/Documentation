---
description: A walkthrough of placing your first perpetuals trade once your account is set up and funded.
---

# Your first trade

This guide picks up after you have an account and a funded perps wallet. If you don't, finish [Create your account](activate-your-account.md) and [Deposit](../managing-funds-and-trading/deposit.md) first.

{% hint style="danger" %}
**Trading risk.** Perpetual trades use leverage. Losses can exceed what you expect, and positions can be liquidated when the price moves against you. Start with an amount you can afford to lose while learning the interface.
{% endhint %}

## 1. Open the Trade interface

Click `Trade` in the left sidebar of the chat page, or go to [copilot.minara.ai](https://copilot.minara.ai) directly. The Perps trading page loads with a price chart on the left and an order panel on the right.

In the top-left, the wallet selector shows which perps wallet your next order will use. Switch to a wallet that holds funds.

At the top of the chart panel, pick an asset (BTC, ETH, SOL, AAPL, XAU, etc.) from the asset selector.

<!-- IMAGE: 建议命名 first-trade-trade-page-overview.png
     内容：Trade 页面整体，标出 wallet selector 和 asset selector 两个位置
     alt text 建议：Perps trading page with the wallet selector top-left and the asset selector at the top of the chart highlighted -->

## 2. Get a Copilot signal (optional)

If you want Minara to suggest a direction:

1. Click `Ask Long` or `Ask Short` in the Copilot panel.
2. Copilot returns a structured signal: entry price, take-profit, stop-loss, and a short rationale.
3. The order panel pre-fills with those values.

If you'd rather place a manual order, skip this step and enter your own values directly in the order panel.

See [Copilot](../../features/trading-copilot.md) for how signals are generated and the parameters you can control.

<!-- IMAGE: 建议命名 first-trade-copilot-signal.png
     内容：Copilot panel 显示一条 long signal（entry / TP / SL / rationale）
     alt text 建议：Copilot panel showing a long signal with entry price, take-profit, stop-loss, and rationale -->

## 3. Review and execute

Before clicking the trade button, check three things in the order panel:

- **Direction** (Long / Short) and **margin mode** (Cross / Isolated)
- **Leverage**: multiplies both gains and losses
- **Take profit and stop loss**: required by Copilot signals, optional on manual orders but strongly recommended

Click `Long` or `Short` to send the order. The order routes to the exchange bound to your selected wallet (Lighter or Hyperliquid). Once filled, the position appears in the `Position` tab at the bottom of the page.

<!-- IMAGE: 建议命名 first-trade-order-panel.png
     内容：order panel 标出 leverage / margin mode / TP/SL / Long/Short 按钮
     alt text 建议：Order panel with leverage, margin mode, TP/SL fields, and Long/Short buttons highlighted -->

## After the trade

- **Monitor and close.** Open positions, PnL, and the manual close action live in the `Position` tab at the bottom of the trading page.
- **Set TP/SL after entry.** If you placed a market order without TP/SL, attach them from the position row using the `Add` action.
- **Move funds out.** Use [Withdraw](../managing-funds-and-trading/deposit.md#withdraw) to send USDC to an external Arbitrum address, or [Transfer between Lighter and Hyperliquid](../managing-funds-and-trading/deposit.md#transfer-between-lighter-and-hyperliquid) to move funds across exchanges inside Minara.

## Next steps

- [Autopilot](../../features/trading-autopilot.md): hand off execution to a managed strategy.
- [Strategy Studio](../../features/strategy-studio.md): write and backtest your own strategies.
- [Liquidations](../../trading-reference/liquidations.md): understand how positions get force-closed.
