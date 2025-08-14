---
description: >-
  This guide shows you how to turn plain prompts into reliable, executable
  workflows in Minara.
---

# Agentic Workflow Best Practice

You’ll learn the key patterns, what to specify in your prompt (asset/chain, trigger, size, risk rules, notifications), and how to validate before going live. Each recipe includes a clean prompt, the nodes Minara will generate, and tips to avoid common pitfalls.

***

**What you’ll build**

> Prompt-to-Agent lets you get creative and try almost anything. AI isn’t perfect, though, so the best practices here highlight use cases that our dev team is focusing on now. Feel free to explore, but you’ll likely get the best outcome by starting with these.

* **Price alert bot** – Monitor token (crypto or stock) moves and push alerts.
* **Trigger order (with TP/SL)** – Set precise entries plus take‑profit/stop‑loss using price triggers + market execution.
* **Sell‑the‑news strategy** – Trade around events: pre‑position, announce‑time action, and post‑event exits.
* **Analysis report** – Schedule Deep Research to deliver a formatted web/PDF report (daily/weekly).
* **Copy trading bot** – Mirror a wallet’s buys/sells (with proportional sizing, caps, and filters).

***

**Before you start**

* Be explicit: **chain**, **token/symbol**, **amount/currency**, **time window**, and **alert channel**.
* Add safety rails: **TP/SL, blacklist tokens, and blacklist wallets.**
* Confirm the canvas first, then **deploy**. Only **Minara Call** nodes (marked with the Minara logo) consumes credits; trades incur fees.

