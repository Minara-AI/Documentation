---
description: >-
  Get notified in real time when a price crosses or stays beyond your level.
---

# Price alerts


{% hint style="info" %}
Automation is available only in the Minara desktop app. The web app and mobile app do not support it yet.
{% endhint %}

A price alert watches a live price and notifies you when your condition is met. Real-time monitoring runs as a simple price check rather than an AI query, so a frequent alert does not burn credits on analysis.

## Two kinds of alerts

| You say                                  | Alert type               | What happens                                                                                                                                                                      |
| ---------------------------------------- | ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "breaks", "crosses above", "drops below" | **When a price crosses** | Notifies you the moment the price moves across your level. If the price is already past the level when you create the alert, it waits for the next crossing.                      |
| "is above", "is below", "higher than"    | **While a price holds**  | Notifies you whenever the price is on your side of the level, including right away if it already is. You choose the minimum time between alerts, or ask for it to fire only once. |

If your wording could mean either, Minara asks which one you want. When you create the alert, Minara also checks the current price and tells you whether it would fire immediately.

## What you can watch

* **Binance** pairs, such as BTC or ETH.
* **Hyperliquid** markets, including crypto, and tokenized stocks and commodities listed there.
* **On-chain tokens** on Ethereum, Base, BSC, Solana, Arbitrum, Optimism, Polygon, and Avalanche. For these, give the chain and the token's contract address.

For assets outside these sources, or for conditions such as "moves more than 5% in a day", Minara can check on a schedule instead. See [Scheduled briefs and reports](scheduled-briefs-and-reports.md).

## Example prompts

* *"Tell me when BTC breaks $120,000."*
* *"Alert me on Telegram if ETH drops below $3,000. Just once."*
* *"While SOL is above $250, remind me every hour."*
* *"Notify me when this Base token 0x... crosses $0.05."*
* *"Alert me when Bitcoin drops more than 5% in a day."*

## Set it up

1. In the desktop app, open **Automations** and describe the alert in the **Chat** tab.
2. Include the asset, the level, the direction, and the channel. For on-chain tokens, include the chain and contract address.
3. Confirm the alert type if Minara asks.
4. Minara saves the alert and turns it on. You can pause it at any time from **Manage**.

## Tips

* **Double-check small tokens.** Copycat tokens with the same name are common. Always confirm the chain and contract address.
* **Use "once" for one-off targets.** An alert that fires once pauses itself afterwards, so you don't get repeated messages.
* **Add context if you want it.** Ask for *"and explain what might have caused the move"* to add a short AI note to each alert. This step uses credits.

## Limitations

* The desktop app must be running to watch prices. Alerts can be missed while it is closed or offline.
* Real-time alerts cover Binance, Hyperliquid, and the on-chain DEX chains listed above.
