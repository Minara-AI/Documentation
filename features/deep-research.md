# Deep Research

Deep Research generates a sourced, structured analysis report on any asset, market, or topic. Type a research question in chat, select Deep Research mode, and Minara produces an interactive report with charts, citations, and key findings.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

***

## How to use it

In the chat interface, type your research question — for example:

> "Create a professional BTC investment analysis report covering macro market trends, key news, technical indicators, ETF data, community sentiment, and capital flows."

Then activate Deep Research mode before submitting. Minara will decompose the question into research tasks, pull data from relevant sources, cross-validate findings, and return a formatted report.

Reports are available as interactive HTML files and can be deployed to a public URL for sharing.

Example output: [https://space.minara.ai/reports/btc-analysis-report-en-0726-1.html](https://space.minara.ai/reports/btc-analysis-report-en-0726-1.html)

***

## What the report includes

A typical Deep Research report covers:

- Key findings and executive summary
- Charts and visualizations from relevant data sources
- Citations linking back to source data
- Contextual analysis organized by research area (technicals, fundamentals, sentiment, etc.)

The structure adapts to the query type. A token analysis report looks different from a macro trend report.

***

## How it works

**Research orchestrator**

Minara decomposes your query into executable tasks and selects the appropriate research approach for each. The orchestrator detects the research context (token analysis, macro overview, project comparison, etc.) and applies the corresponding methodology. It dynamically adjusts depth and scope based on what the initial data returns.

**Data layer**

Minara pulls from over 50 integrated data providers covering price data, on-chain metrics, social sentiment, DeFi activity, and macro indicators. See the full [tools integration list](../technology/tools-integration.md).

**Analysis synthesizer**

The synthesizer processes collected data, identifies patterns across sources, cross-checks for consistency, and generates the final report. It handles structured API data, unstructured text, and time-series data in a single pass.

If a response is interrupted due to a system error, no credits are deducted.
