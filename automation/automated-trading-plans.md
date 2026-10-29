---
description: >-
  Turn a simple trading plan into an automation: recurring buys, laddered orders, or mirroring a wallet's trades within your limits.
---

# Automated trading plans


{% hint style="info" %}
Automation is available only in the Minara desktop app. The web app and mobile app do not support it yet.
{% endhint %}

An automated trading plan carries out rules you define: buy on a schedule, place orders across a price range, or follow another wallet's trades within limits you set. You stay in control of every money move unless you choose otherwise.

## Templates

| Template                     | What it does                                                                           | Starting prompt                                                                                                                                                                           |
| ---------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Recurring buy plan**       | Buys a token on a schedule, buying more when the price is low and less when it is high | *"Set up a recurring buy plan for a token I choose. Buy more when the price is low and less when it's high, on a daily schedule, and ask me to confirm each buy before it goes through."* |
| **Ladder buy and sell**      | Places staggered buy or sell orders across a price range                               | *"Place a series of laddered buy or sell orders for a token across a price range I set."*                                                                                                 |
| **Mirror a wallet's trades** | Follows a wallet's trades with a fixed amount per trade and a daily spending cap       | *"Mirror the trades of a wallet I choose, with a fixed amount per trade and a daily spending cap, and ask me before each trade."*                                                         |

You can also combine a [price alert](price-alerts.md) with a trade, for example *"If ETH drops to $3,000, buy $500 worth and notify me."*

## How Minara keeps you in control

* **It asks before it builds.** Minara confirms the asset, wallet, trade size, leverage, and limits before saving a plan that trades.
* **Trades wait for you by default.** When a run reaches a trade, it pauses with **Waiting for your approval**. Click **Approve** to place it or **Reject** to skip it.
* **Tests never trade.** **Test** shows you what the plan would do, without placing orders.
* **You choose the permission level.** In the automation's **Execution permissions**, every mode except **Hands-off** still asks you to confirm money moves. See [Approvals and permissions](overview.md#approvals-and-permissions).

{% hint style="warning" %}
With **Hands-off**, trades and transfers run without asking you first. Use it only after you have tested the plan, set a spending cap, and are comfortable with the worst case.
{% endhint %}

## Set it up

1. In the desktop app, open **Automations** and pick a template, or describe the plan in the **Chat** tab.
2. Answer Minara's questions about the asset, amount per trade, schedule or price range, wallet, and any caps.
3. Review the flow on the canvas. Check every step that moves money.
4. Click **Test** to preview the trades without executing them.
5. Turn on **Automatic execution**. Approve each trade as it comes in, or adjust the permission level once you trust the plan.

## Tips

* **Start small.** Use a small amount per trade until you have watched a few runs.
* **Set caps.** A per-trade amount and a daily spending cap limit the damage if a market moves fast or a followed wallet behaves unexpectedly.
* **Vet wallets before following them.** Many active wallets belong to insiders or short-term traders. Past trades don't guarantee future results.
* **Watch your balance and credits.** A plan can't trade without enough funds, and AI steps in the plan consume credits.

## Limitations

* The desktop app must be running for plans to trigger. Runs can be delayed or missed while it is closed or offline.
* Wallet-following plans react to detected activity. They can lag the original trade, and the price you get may differ.
* For quantitative strategies that should run continuously with risk controls, use [Autopilot](../features/trading-autopilot.md) or [Strategy Studio](../trade/strategy-studio/README.md).

All trading involves risk. Automations follow your rules; they do not guarantee profits.
