---
description: Answers to common questions about Minara.
hidden: true
noIndex: true
---

# FAQs

***

## Getting started

### How do I ask questions in Minara?

Open the chat window and type any question or request. No special commands are needed. Examples:

- "Is it a good time to buy ETH now?"
- "Analyze the BTC market for the next week."
- "Buy $100 of ETH for me."

Minara understands context across a conversation. You can follow up with shortened requests like "buy $10 more" or "cancel the last order." Technical analysis, market research, and trade execution can all happen in one chat thread.

### What can Minara help me with?

Minara covers the full cycle from data analysis to execution:

- Market analysis and trade signals for crypto and stocks
- On-chain data, wallet tracking, and DeFi activity
- Deep Research reports on tokens, projects, or macro topics
- Perpetual and spot trade execution
- Automated strategy execution via Autopilot
- Workflow automation for copy trading, DCA, and alerts

### Where do I manage my subscription?

Click **Manage** in the top right corner. From there you can view your current plan, credit usage, billing cycle, and upgrade or downgrade options. Upgrades take effect immediately; downgrades take effect at the next billing cycle.

See [Subscription & Top-up Policy](subscription-and-credits/subscription-and-top-up-policy.md) for full details.

### How many credits does a query cost?

Credit consumption depends on the complexity of the query and the tools it invokes. Typical estimates:

- Standard chat message: ~20 credits
- Deep Research report: ~40 credits

See [How Credits Work](subscription-and-credits/how-credits-work.md) for the full breakdown.

### What are Bonus Sparks?

Bonus Sparks are extra reward points included in some subscription plans. More Spark-based features will be introduced in [spark.md](ecosystem/spark.md). Credits and Sparks are separate — credits meter AI usage, Sparks are for rewards.

***

## Trading and assets

### What assets and chains does Minara support?

**Perpetuals:** traded on Hyperliquid. All assets supported by Hyperliquid are available.

**Spot:** Solana, Ethereum, Base, BNB Chain, Arbitrum, Optimism, Polygon, Avalanche. Cross-chain trades are handled automatically — Minara bridges assets behind the scenes without requiring manual network switching.

### What is the minimum deposit?

The minimum transfer into the Perps Wallet is 10 USDC. For spot trading, there is no enforced minimum, but network fees apply on every transaction.

### What is the difference between Copilot and Autopilot?

**Copilot** generates a trade signal — entry price, take-profit, stop-loss, and rationale — when you ask for one. You review the signal and decide whether to execute. You are in control of every trade.

**Autopilot** runs a strategy continuously without requiring your input. It opens and closes positions, sets TP/SL orders, trails stops, and handles risk controls automatically based on predefined strategy logic. You authorize the trading scope and can override or stop it at any time.

### How do I set a stop-loss on an open position?

Go to Trade > Positions, select a position, and click "Add." Enter your TP and/or SL values in the input fields, add split targets if needed, and confirm. Your stop-loss is now active on that position.

See [Trading Copilot](features/trading-copilot.md) for a step-by-step guide with screenshots.

### How do I check my transaction history?

Click **Asset > Activity** to view your full transaction history and account activity.

{% columns %}
{% column %}
<figure><img src=".gitbook/assets/图片 (26).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src=".gitbook/assets/图片 (8).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

### Will Minara execute trades without my authorization?

No. Minara requires explicit confirmation before executing any trade. Large transactions trigger a secondary confirmation. Automated strategies (copy trading, DCA, Autopilot) only run after you have set and started them. You can pause, modify, or stop any strategy at any time.

### How does Minara handle a failed trade?

Before execution, Minara checks balance, gas fees, and slippage settings. If a trade fails due to network congestion or price movement, Minara adjusts gas and retries. If the trade ultimately fails, you receive a detailed error analysis. All operations are logged and visible in your Activity history.

***

## Deposits and withdrawals

### My deposit has not arrived — what should I do?

Most deposits complete within 5–30 minutes. If yours takes longer:

1. Verify that you used the correct deposit chain and address.
2. Check the blockchain explorer to confirm the transaction was processed on-chain.
3. If it is confirmed on-chain but your balance has not updated, contact support via the [official Discord](https://discord.com/invite/minaraai).

### Why was my on-chain withdrawal rejected?

Common reasons:

- Insufficient balance to cover gas fees
- Invalid withdrawal address format
- Network mismatch between the selected network and the withdrawal address

Check each of these before retrying. If the problem continues, contact support via Discord.

### Why can't I deposit SOL from Binance to Minara?

Minara uses AA+ custodial wallets. Binance's mobile app does not currently support withdrawals to this wallet architecture. To deposit SOL, use Binance Web, or deposit via BNB Chain or another supported chain instead.

### I deposited tokens from an unsupported chain — what do I do?

Contact support via the [official Discord](https://discord.com/invite/minaraai). Recovery is not guaranteed. Common reasons assets cannot be recovered: sending via an unsupported blockchain, or sending to an incorrect address.

***

## Credit card deposits

### What if my credit card deposit fails?

Due to bank risk controls and regional payment policies, card payments may fail. Try a different card or payment method. You can also deposit crypto directly into your Minara wallet from another wallet or exchange.

### I paid but have not received crypto — what do I do?

If the transaction failed, your funds are typically refunded to the original payment method automatically. If you have not received crypto or a refund after 24 hours, contact the OTC provider directly with your payment proof and order ID:

- **Alchemy Pay:** [https://ramp.alchemypay.org/](https://ramp.alchemypay.org/)
- **Banxa Pay:** [https://support.banxa.com/en/support](https://support.banxa.com/en/support)
- **Kodo Finance:** [https://global.kodo.finance/](https://global.kodo.finance/)

Minara aggregates these third-party OTC providers but does not operate them.

### Why did I receive less crypto than I paid for?

This is normal and typically due to platform fees, exchange rate slippage, payment provider fees, or gas fees. If the difference seems unusually large, contact the OTC provider with your transaction details and receipt.

### Why did KYC fail?

OTC providers have varying KYC requirements by country and bank. Try a different card, a different payment method, or contact the provider's support directly.

***

## Troubleshooting

### What if Minara's answer seems inaccurate?

For factual data errors (price, volume, TVL), follow up with a specific request: "The BTC price you gave me looks wrong. Please re-fetch and try again." Minara pulls from multiple providers (CoinMarketCap, DeFiLlama, DexScreener, etc.) and short-term deviations can occur for low-liquidity or newly listed assets.

For interpretation disagreements, prompt Minara to show both sides rather than just pushing back:

- "Re-analyze BTC and show which signals support bullish vs. bearish."
- "Give me both a bullish and a bearish case, then tell me which appears stronger."

Asking Minara to show conflicting evidence produces more reliable analysis than asking it to reverse its conclusion.

### Why is Minara not giving any output?

1. Check that your credits have not run out and your subscription has not expired.
2. Refresh the page or start a new chat, then retry.
3. If there is still no output, contact support via the [official Discord](https://discord.com/invite/minaraai).

### Why can't I access Minara?

Common causes:

- Access from a restricted region (Mainland China, North Korea, etc.)
- Network connectivity issue — check other sites first
- Browser issue — clear cache and cookies, try incognito mode, or switch browsers
- On mobile — try switching between Wi-Fi and mobile data

If problems persist, contact support via the official Discord.

### My data is not syncing between mobile and desktop — what should I do?

Make sure you are logged into the same account on both devices, then refresh or log in again. The web version on Chrome (desktop) is currently the recommended primary interface. A native mobile app is in development.

### What if my account is compromised?

1. Change the password for your login method (email or Google) immediately.
2. Log in to Minara and check the Activity page for suspicious transactions.
3. Consider pausing all automated strategies.
4. Transfer assets to a secure wallet.
5. If there is any asset loss, preserve screenshots and transaction records for investigation.

***

## Data and AI accuracy

### What data sources does Minara use?

Minara integrates over 50 data providers via API, including Arkham, CoinMarketCap, Glassnode, NFTGo, and DeFiLlama. Data is not sourced from web searches. All key data in analysis responses is labeled with its source — you can click through to the original data.

### What should I do if Minara produces incorrect information?

Point it out directly. Minara will re-verify and correct. For critical investment decisions, ask Minara to provide source links and cross-check with external data. AI systems can produce errors, and your feedback improves accuracy over time.
