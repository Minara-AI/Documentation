# Deep Research

## Overview

Minara leverages its AI-powered deep research engine to deliver institutional-grade analysis for every user. It enables comprehensive research on any crypto project, stock, market, or trend—without requiring domain expertise or expensive data subscriptions.

Unlike other research tools that rely on static data or web pages or simple aggregation, Minara’s engine uses dynamic and agentic workflows that adapt based on query complexity and context. It handles multiple data streams in parallel, cross-validates findings, and generates real-time, professional-grade reports.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

## Core Components

### Research Orchestrator

A smart workflow engine that decomposes complex queries into executable tasks, selects optimal research strategies, and coordinates data collection. Built on LangGraph-based state management, it includes:

* **Scenario-Based Planning**: Detects research context (e.g. token analysis, macro insights) and applies specialized methodologies.
* **Task Decomposition**: Uses structured prompting and pattern validation to turn abstract questions into actionable goals.
* **Adaptive Workflow Management**: Dynamically adjusts research depth and scope based on initial findings and data quality.
* **Streamed Progress Updates**: Real-time transparency through Stream-based progress feeds.

### Data Ecosystem

A unified API layer integrating over 50 professional tools and data sources. It provides real-time access to market data, on-chain metrics, social sentiment, macro indicators, and project fundamentals.&#x20;

You can check our tools integration at this [doc](tools-integration.md).

### Analysis Synthesizer

An AI-powered engine that processes collected data, identifies insights, cross-checks sources, and generates coherent, citation-rich reports. It supports structured APIs, unstructured text, and time-series data via:

* **Cross-Validation Engine**: Ensures consistency and reliability across sources.
* **Contextual Analysis Framework**: Applies domain-specific reasoning models for various research types.
* **Report Generation Pipeline**: Outputs professional reports in HTML, PDF, or Markdown with visualizations and executive summaries.

## Showcase

Minara generates analysis reports in PDF and **interactive** HTML file, supporting deployment to publicly accessible static websites.

Here's the example:

> **Send the prompt below to Minara:**&#x20;
>
> "Create a professional BTC investment analysis report with rich visuals and in-depth insights, which covers all key aspects, including macro market trends, major news, short- and long-term technical indicators, ETF data, community sentiment, capital inflows and outflows, and investment strategies."

And you'll get the report: [https://space.minara.ai/reports/btc-analysis-report-en-0726-1.html](https://space.minara.ai/reports/btc-analysis-report-en-0726-1.html)
