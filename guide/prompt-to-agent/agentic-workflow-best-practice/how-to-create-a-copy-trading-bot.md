---
description: >-
  Automatically mirror trusted wallet buy and sell strategies with Minara
  workflows, no manual effort needed.
---

# How to create a copy trading bot?

### What you’ll build

* A workflow that monitors target wallets on-chain
* Auto-executes the same buy/sell trades with your Minara wallet
* Supports spot tokens on supported chains

***

### Step-by-step

1. **Pick wallets to follow**
   * Get the wallet address you want to copy (e.g., `0x1234...abcd`).
   * Make sure this is an active trader with real volume — copying inactive or “spam” wallets won’t help.
   * You may select mutiple wallets to monitor and mirror in one workflow.
2. **Create a workflow in Minara**
   *   Prompt example:

       > “Watch this wallet DbrdV2...(a wallet address) on the Solana chain, and copy each buy/sell action with $50 per trade.”
3. **Set execution rules**
   * Use fixed trade amounts (e.g., $50 per order) for predictability and easier risk control.
4. **Choose notification method**
   * Receive trade execution notification via email or telegram.
5. **Deploy and monitor**
   * The bot will monitor the wallet’s on-chain activity.
   * When a supported trade is detected, Minara will mirror it following your rules.
   * You’ll receive a notification each time a trade is executed.

***

### Best Practices

* **Vet before you follow**: Many wallets belong to insiders or short-term memecoin players — research before copying.
* **Start small**: Test with small balances first to check execution accuracy.
* **Asset whitelist/blacklist:** only copy certain tokens, or exclude risky memecoins.

***

### Current Limitations

* Only spot token trades are supported.
* Copying is limited to supported chains detected by the Monitor system.

***

### Future Developments

* Proportional trade sizing (e.g., match 10% of their position size).
* Risk Control (e.g. setting daily/weekly spend limits)
* Smarter filters (e.g., copy only if trade > $10,000, or exclude tokens under $1M market cap)
* Portfolio mirroring (not just individual trades)
* Futures and leverage support
