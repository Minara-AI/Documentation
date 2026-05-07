---
description: How Minara credits are consumed, what uses credits, and what does not.
---

# How credits work

Credits measure your AI usage on Minara. They are deducted when you complete an action that requires AI processing. Autopilot execution and Copilot position management do not consume credits.

Credits reset at the start of each billing cycle. Unused credits do not carry over.

***

## What consumes credits

- Chat messages sent to Minara
- Deep Research report generation
- Workflow nodes that call Minara's AI (Minara Call nodes)

If a response or task is interrupted due to a system error, no credits are deducted.

## What does not consume credits

- Autopilot opening, managing, and closing positions
- Copilot generating trade signals
- Viewing your portfolio or trade history
- Running Monitor, Trade, or Notify nodes in a workflow

***

## Estimated credit costs

Credit consumption varies by query type and complexity. The values below are averages for reference only.

| Action | Estimated credits per action |
| --- | --- |
| Chat message | ~20 credits |
| Deep Research report | ~40 credits |
| Minara Call node in workflow | ~15 credits |

Longer or more complex queries (for example, Deep Research on a less-covered topic with many data sources) may use more credits than the estimates above.

***

## Workflow node credit usage

| Node type | Credit usage |
| --- | --- |
| Monitor | Currently free |
| Trade | Free |
| Notify | Currently free |
| Minara Call | Based on actual tokens used |

All running workflows pause if your credits run out, regardless of node type.

***

## Getting more credits

Credits reset at the start of each new billing cycle. If you run out before then, you have two options:

- **Upgrade your plan** — takes effect immediately and adds the new plan's credit allocation at the price difference
- **Purchase a top-up credit pack** — available only on paid plans and only after your subscription credits are fully consumed

See [Subscription & Top-up Policy](subscription-and-top-up-policy.md) for upgrade and top-up rules.
