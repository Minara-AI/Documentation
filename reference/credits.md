# Credits

Credits are Minara's metering unit for AI usage. You spend credits whenever Minara's models do work for you: chat, research, scheduled analyses, API calls. Trades themselves are charged separately as trading fees, not in credits.

## How you get credits

Credits come with a Minara subscription. Each paid plan tops up your balance on its renewal cycle, and annual billing is available.

If your subscription expires, your balance resets to the Free plan's 300 credits.

## Plans

<!-- IMAGE: 建议命名 manage-credits-plans.png
     内容：完整的 Manage 弹窗截图（你在对话里发的那张），显示 Free plan 状态 + Lite / Starter / Pro 三个付费 plan 卡片
     alt text 建议：Manage plan dialog showing the Free plan status and Lite, Starter, Pro paid plans with credits, price, and features -->

Individual plans are available from the **Manage** dialog (top-right account menu in the web app, or ask Minara in chat to "manage credits"):

| Plan    | Price     | Credits | Active workflows | Agent          | Notes                                           |
|---------|-----------|---------|------------------|----------------|-------------------------------------------------|
| Free    | $0        | 300     | —                | —              | —                                               |
| Lite    | $19 / mo  | 1,400   | 5                | Smarter Agent  | 190 bonus Sparks                                |
| Starter | $49 / mo  | 4,000   | 20               | Smarter Agent  | Standard priority; 490 bonus Sparks             |
| Pro     | $199 / mo | 20,000  | 50               | Smartest Agent | API access; higher priority; 1,990 bonus Sparks |

All paid plans include unlimited Copilot and Autopilot, custom strategy deploy and run, and full feature access. Business plans are available in the same dialog under the **Business** tab.

Bonus Sparks are a separate reward currency for ecosystem perks (badges, NFT whitelists, event entry).

## What consumes credits

* Chat queries, research reports, and Crypto Picks.
* Workflow nodes marked with the Minara logo ("Minara Call" nodes). Other workflow components such as price-alert triggers and conditions run on the backend and do not consume credits.
* Scheduled analyses. Each scheduled run consumes credits, so pick a frequency that matches how often you actually need fresh output.
* All [Agent API](../trade/agent-api/api-key.md) calls authenticated with an API key.

## What doesn't consume credits

* The trades themselves. Trading is metered as [trading fees](../trade/trading-fees.md), separately from credits.
* Wallet operations: deposits, withdrawals, balance checks.
* Price-alert monitoring, which runs on Minara's backend rather than as AI queries.

## When credits run out

For Agent API requests, calls pause until your balance is replenished, either at your next renewal or after upgrading your plan.
