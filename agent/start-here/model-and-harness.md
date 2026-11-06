# Model and Harness

Minara separates reasoning from runtime authority. The model proposes and explains. The harness controls context, tool access, memory, execution, and review gates.

<figure><img src="../.gitbook/assets/Frame 372.png" alt=""><figcaption></figcaption></figure>

## The model reasons

The model reads the current prompt, compares evidence, drafts plans, asks follow-up questions, and explains its conclusions.

It can decide that a source is missing, a conclusion is weak, or a next step should be reviewed by the user. It can also propose tool calls and code changes. That is still reasoning. It is not authority.

## The harness governs

The harness decides what the model can see, which tools are available, where code runs, what memory is retrieved, and when a user must approve an action.

| Layer     | Responsibility                                                                       |
| --------- | ------------------------------------------------------------------------------------ |
| Context   | Select instructions, workspace state, memory, tool results, and relevant records.    |
| Tools     | Expose capabilities through typed calls and return observations to the conversation. |
| Workspace | Give the task a place to read, write, run code, and preserve artifacts.              |
| Memory    | Retrieve useful history without turning it into permission.                          |
| Safety    | Enforce review and authorization before consequential actions.                       |
| Handoff   | Preserve what changed, what was checked, and what remains uncertain.                 |

## Why the separation matters

Financial work has different risk levels. Reading a market page, editing a local file, previewing an order, and confirming a trade cannot share the same permission model. The harness keeps those boundaries explicit.

For example:

* reading BTC funding data should be easy;
* preparing an order preview should show assumptions and risk;
* confirming the order requires verified user authorization;
* remembering that a user usually prefers conservative leverage is useful context, not current consent.

This separation also keeps the product extensible. A new tool, source, model, or runtime can be added without pretending the model itself owns the operating boundary.

## What users should expect

Users should expect the agent to explain its work, cite the surfaces it used, and stop when a step needs approval. They should not expect a model answer to bypass configured controls, reveal credentials, or silently move funds.
