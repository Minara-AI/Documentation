---
description: >-
  This page explains the mechanism of Minara's Prompt-to-Agent feature. Learn
  about its underlying architecture, supported node types, and usage rules.
---

# How Prompt-to-Agent works

***

### Core Mechanism

Minara's workflow engine is built upon the open-source platform [n8n](https://n8n.io/), a visual automation tool that enables the creation of complex workflows through a node-based interface.

When you chat with Minara, she recognizes your intent and parses your command to identify executable tasks. These tasks are then translated into workflows and displayed visually as nodes and branches on a canvas. This approach enables users to:

* **Visualize Workflow Logic**: Understand the sequence and dependencies of tasks.
* **Monitor Workflow Status**: Track the execution of each workflow, even performance (coming soon).
* **Manage Workflows**: Deploy, pause, resume, or edit manually (coming soon).

Currently, a workflow can only be modified through follow-up prompts to Minara in the same chat where it's created, and only modifiable before it gets deployed.&#x20;

***

### &#x20;Supported Node Types

Minara's workflows are composed of various node types, each serving a specific function:

1. **Monitor Triggers**:
   * **Token Price Monitoring**: Monitor price changes of specific tokens. (e.g. "When ETH breaks through $4000")
   * **Wallet Activity Monitoring**: Track buy or sell transactions from a wallet address.
2. **Time-Based Triggers**:
   * **Delayed Start**: Trigger a workflow after a specified delay. (e.g., today at 3 PM)
   * **Scheduled Start**: Execute workflows at predefined intervals (e.g., daily at 8 AM).
3. **Conditional Logic**:
   * **If Condition**: Evaluate conditions and direct the workflow based on the outcome.
4. **Action Nodes**:
   * **Notify**:
     * **Email**: Send alerts to the email or Gmail that links to the user account.
     * **Telegram**: Dispatch messages via Telegram bot (requires user to provide `chat_id`).
   * **Trade**:
     * **Market Orders**: Execute buy/sell orders on supported blockchains (Base, Ethereum, Solana).
     * **Stop Market Orders**: Combine token price triggers with market orders for automated trading.
   * **Minara Call**:
     * Send prompts to Minara to get responses. Deep Research mode available.

***

### Important Usage Notes

* **Credit Consumption**: For now, only the **Minara Call** node consumes credits.
  * However, successful trading actions will incur transaction fees, like other trades done with Minara.
* **Workflow Execution**: If your credit balance is depleted, all active workflows will be automatically paused. To avoid unexpected losses from execution interruptions, please make sure that you have sufficient credits.

For more details about credits, please refer to: [subscription-and-credits](../../subscription-and-credits/ "mention")

***
