---
description: >-
  By setting order triggers, Minara place trades automatically when your target
  triggers are hit.
---

# How to set up automated trade execution

Minara can watch for specific price conditions and automatically place orders when they’re met — perfect for buying the dip, taking profits, or setting stop-losses without constant manual monitoring.

***

### What You’ll Build

A workflow that:

* Monitors the **absolute price** of a token (≥ or ≤ a set value)
* Executes **buy, sell, or both** when the condition is met, including **take-profit (TP)** and/or **stop-loss (SL)** strategies
* Sends you a notification confirming the execution

> Price monitoring is handled by our monitor system — real-time and reliable, but only for supported tokens on supported chains.

***

### Example Prompts

You can simply describe the order logic you want. Minara will translate it into a workflow that uses our dedicated monitor system for high-precision execution.

1.  **Simple Buy/Sell Trigger**

    > "If ETH price falls to 4,000 USDT, buy $500 worth of ETH."
    >
    > "If BTC price reaches 130,000 USDT, sell 0.1 BTC."
2.  **Buy + TP/SL Strategy**

    > "Buy 200 USDT of SOL if price ≤ 175 USDT, then take profit at 200 USDT and stop loss at 160 USDT."
3.  **Laddered Buy**

    > "Buy $200 ETH at 4,000 USDT, $200 at 4,150 USDT, and $200 at 4,250 USDT."
4.  **Partial Exit**

    > "If DOGE price hits 0.25 USDT, sell half my position."

***

### Best Practices

* Use **limit orders with TP/SL** for better risk management.
* Keep your telegram account linked and [Minara notification bot](https://t.me/MinaraNotificationBot) enabled to get real-time execution updates.
* Check spam folder first if you didn't receive the execution result email that you should've received.
* Avoid unnecessarily small TP/SL gaps — sudden price wicks can trigger premature exits.
* For small‑cap meme tokens, copycats and same‑name lookalikes are common—especially during hype. To avoid mistakes, always specify and double‑check the chain and the token’s contract address.

> Mainstream assets like BTC, ETH, or SOL are already disambiguated by contract.

***

### Future Developments

* Percentage-based triggers (e.g., +5% in 24h)
* Futures, leverage, and advanced strategies for order triggers.
* Multi-condition orders (e.g., trigger only if price condition + volume spike)
* Auto-adjusting stop-loss (trailing SL)
* More trigger types (e.g. news trigger for sell-the-news strategy)
