---
description: >-
  Build a reliable alert that watches prices and pings you the moment conditions
  hit.
---

# How to create a price alert bot?

With Minara's monitor system, you can set high-precision, real-time alerts for token prices without worrying about delays or missed triggers. When the set price condition is met, Minara can instantly notify you without consuming any credits.

***

### What to Expect

* **High-precision, real-time monitoring** for **token absolute prices**\
  (e.g., “Alert me when SOL hits $150”).
* Works for **on-chain tokens** and **tokenized stocks**.\
  Non-tokenized stock prices and price change percentage alerts are **not yet supported** in real-time mode.
* Alerts can be sent via telegram or email.
* **No credit consumption** — the monitoring is done on our backend, not by repeated AI queries.

***

### Example Prompts

* _“Alert me when **ETH** drops to **$4,000**.”_
* _“Email me if **SOL** rises above **$180**.”_
* _“When **DOGE** hits **$0.28**, send me an alert.”_

***

### How It Works

1. **You tell Minara the asset and target price**.
2. Minara registers your alert in the monitor system.
3. The monitor system continuously tracks the token price in real time.
4. Once the price crosses your target, the monitor will trigger the workflow to send you an alert immediately.

***

### Best Practice

* **Use absolute price triggers** (≥ / ≤) . Real-time % change tracking is not yet available.
* Keep your telegram account linked and [Minara notification bot](https://t.me/MinaraNotificationBot) enabled to ensure delivery.
* Check spam folder first if you didn't receive the alert email.
* For small‑cap meme tokens, copycats and same‑name lookalikes are common—especially during hype. To avoid mistakes, always specify and double‑check the chain and the token’s contract address.

> Mainstream assets like BTC, ETH, or SOL are already disambiguated by contract.

***

### Future Developments

Minara is planning to support:

* Percentage-based alerts (e.g., ±5% in 1h)
* Non-tokenized stock prices in real time
* Browser Push notifications
* Auto-recurring notification bots — monitors and alerts will run continuously

You _can_ still track these via workflows by scheduling periodic checks, but each check will be conducted by Minara AI and consume credits — which can become costly for high-frequency setups.

\
We recommend reserving this approach for low-frequency use cases. For example:

* **Weekly market health check** — Review market cap trends and macro indicators every Friday.
* **Monthly asset performance review** — Pull 30-day price change data for your top 5 holdings on the first day of each month.
* **Long-term target tracking** — Every Friday, evaluate our market bias by reviewing all bull- and bear-market top indicators.

To explore more about the use cases above, please check out&#x20;

