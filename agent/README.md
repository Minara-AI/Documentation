---
description: >-
  The design behind Minara's financial agent: controlled actions, focused
  context, trading memory, data access, and coding workflows.
---

# Minara Harness

An intelligent model can reason about a market. A useful financial agent also needs the context, tools, and boundaries to act on that reasoning.

Minara Harness is the system around the model that brings these pieces together. It connects research to execution, keeps relevant experience available, and places consequential actions behind explicit controls.

* **Grounded work:** connect reasoning with relevant context and tools.
* **Controlled action:** enforce boundaries around funds, files, and execution.
* **Continuity:** retain useful experience and reusable artifacts.

<figure><img src=".gitbook/assets/Frame 372.png" alt=""><figcaption></figcaption></figure>

## Model and harness

Our design starts with a separation of responsibilities: the model reasons and proposes; the harness manages context, access, and execution.

This lets the agent work across research, analysis, and action without treating every task the same way. Reading market data should be easy. Running code needs an appropriate environment. Moving funds needs valid authorization. Remembering a past decision should improve context, not silently grant permission for a new one.

## What users can do with it

Minara Harness shows up through practical desktop workflows:

* scan TradFi and crypto markets before deeper research;
* ask Copilot focused questions about an asset page;
* review market, leverage, funding, and liquidation context before preparing an order;
* inspect portfolio scope before asking exposure questions;
* compare strategy backtests, marketplace filters, and strategy details;
* build strategy drafts from structured inputs;
* create recurring research and thesis trackers;
* enable computer control for explicit, bounded desktop tasks;
* run multi-perspective investment reviews.

See [Use Cases](start-here/use-cases/) for tested desktop examples and screenshots.

## Safety by design

Financial actions deserve stronger boundaries than ordinary tool use. Tools declare their control requirements, and the harness enforces the applicable authorization checks before execution. A model-supplied parameter claiming confirmation is not evidence of user consent.

The design supports both interactive decisions and explicitly authorized workflows. The central principle is that financial authority comes from the user's permissions and the system's enforcement—not from the model deciding that an action is reasonable.

Financial gates work alongside file-access policies, protected-path checks, credential handling, and execution isolation. Secret-management tools provide names and masked status rather than raw credential values; the execution environment governs how configured credentials can be used.

These safeguards address different risks. Access to files or code execution does not grant permission to move funds, and a workspace alone is not a complete security boundary. The exact isolation depends on the deployment. Safety controls authority and execution flow; it does not remove market risk or guarantee an outcome.

## Memory and self-learning

A financial agent should not start from scratch with every conversation. Relevant trading activity, captured decisions, and past experience can provide continuity across tasks.

Trading memory connects available activity with captured reasoning and later evidence. When the relevant learning features are enabled, a self-learning loop can turn selected experiences into retained guidance for future tasks: observe, reflect, and reuse.

The goal is a more informed assistant that can revisit earlier reasoning and refine its working methods. Memory improves the context available to the model; it is not automatic retraining after each trade, and a remembered preference is not current trading consent.

## Focused context

A session connects working files with a retrievable conversation history. The transcript preserves recorded exchanges; the model's current context and reusable memory serve different purposes.

Progressive disclosure extends the same idea to tools: keep common capabilities readily available, discover specialized tools when needed, and load their parameter definitions on demand. Rather than filling the context with definitions for every connected data source and service, the harness reveals relevant capabilities as the task develops. The aim is both lower token overhead and less distraction from irrelevant or overlapping tool descriptions, keeping the model focused on the task without removing permission checks.

## Multi-source tools

Financial reasoning benefits from more than a single feed. Minara brings market data, news, account information, and other available research tools into a shared workflow, allowing the agent to gather evidence suited to the question.

The design preserves meaningful differences between sources: which asset or venue a value describes, how recent it is, and whether it is a reference price or an execution quote. Multiple sources broaden coverage and enable comparison; they do not automatically establish agreement or accuracy.

When evidence is incomplete or conflicting, the agent should make that uncertainty visible rather than turn it into false precision.

## Coding workflows

Minara also supports coding work within this harness: inspecting projects, writing analysis scripts, changing implementations, and checking results. The workspace preserves useful artifacts for review and reuse, while file, credential, and execution protections continue to apply. The goal is a working, reviewable result that respects the user's existing work and requested scope.

## A connected workflow

These capabilities work together around the agent loop. A request brings in relevant context; tools provide observations; safety controls govern consequential actions; and results return to the conversation. Files and supported records can then preserve useful outputs beyond the immediate task.

The aim is not simply to give a model more tools. It is to make financial work more coherent: research grounded in evidence, actions tied to authority, execution bounded by its environment, and experience available for future decisions.

## Explore the harness

* [Use Cases](start-here/use-cases/) — practical desktop workflows grounded in tested screenshots.
* [Task Walkthrough](start-here/task-walkthrough.md) — one complete research-to-review path.
* [Session Workspace](core-concepts/session-workspace.md) — where task files, runtime context, and desktop bridges fit.
* [Financial Authorization](operate-safely/financial-authorization.md) — the boundary between research, preview, and action.
* [Market Tools](build-and-extend/market-tools.md) — multi-source access and informed interpretation.
* [Capability Map](build-and-extend/capability-map.md) — a quick map of tools, memory, automation, coding, and safety controls.
