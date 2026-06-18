# Research and analysis

The Minara chat input has three modes. **Chat** is the default where you start typing and Minara answers conversationally. To switch to **Deep Research** or **Data Visualization**, type `/` in the input field and pick a mode from the slash menu.

***

## Chat

The default mode. Ask any question about crypto, stocks, commodities, or macro. Minara queries its data sources in real time and responds in conversational format. Use this for price checks, quick analysis, trade signals, on-chain lookups, and follow-up questions.

**Common examples:** checking BTC price and on-chain metrics, reviewing ETH funding rates, looking up SOL whale activity, or asking about GOLD ($XAU) macro positioning.

**Speed toggle**: in Chat mode, you can switch between two response depths using the toggle on the right side of the input:

* **Fast**: clear, concise answers with fewer reasoning steps. Good for quick checks.
* **Quality**: thorough explanations with structured insights. Use for complex analysis or trade decisions.

<figure><img src="../.gitbook/assets/01-fast-quality-dropdown.png" alt=""><figcaption></figcaption></figure>

***

## Deep Research

**How to activate:** type `/` in the input and select **Deep Research** from the slash menu. The input shows a `Deep Research` chip once the mode is active; click the `×` on the chip to return to Chat.

Deep Research runs a multi-stage research workflow instead of responding immediately. Minara decomposes your question into tasks, queries multiple data sources in parallel, cross-validates findings, and produces a structured report with charts, citations, and an executive summary.

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/02-slash-menu.png" alt=""><figcaption></figcaption></figure>

_Slash menu_
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/03-deep-research-active.png" alt=""><figcaption></figcaption></figure>

_Deep Research mode activated_
{% endcolumn %}
{% endcolumns %}

Use Deep Research when you need a shareable, source-backed output rather than a quick answer. For example: a fund memo on Ethereum's competitive positioning, a macro analysis of gold versus Bitcoin in a risk-off environment, or a sector overview of AI-related stocks like NVIDIA (NVDA), Microsoft (MSFT), and Amazon (AMZN).

Output is downloadable as PDF or Word.

**When to use Deep Research vs Chat:**

|               | Chat                        | Deep Research                    |
| ------------- | --------------------------- | -------------------------------- |
| Response time | Seconds                     | 1–3 minutes                      |
| Output format | Conversational              | Structured report with sections  |
| Best for      | Quick decisions, follow-ups | In-depth analysis, documentation |
| Downloadable  | No                          | Yes (PDF / Word)                 |

***

## Data Visualization

**How to activate:** type `/` in the input and select **Data Visualization** from the slash menu. The input shows a `Data Visualization` chip once the mode is active; click the `×` on the chip to return to Chat.

Data Visualization turns your question into structured data output — tables, charts, and visual breakdowns — instead of long-form prose. Minara picks the chart type that fits the question (line, bar, comparison table, distribution, etc.) and renders it inline in the chat.

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/02-slash-menu.png" alt=""><figcaption></figcaption></figure>

_Slash menu_
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

_Data Visualization mode activated_
{% endcolumn %}
{% endcolumns %}

**Available chart types:** Lines, Bars, Pie, Candles, Funnel, Scatter, Heatmap, Radar, Calendar, Treemap, Sankey, Sunburst, Network, Gauge.

**When to use Data Visualization:**

* Comparing multiple assets across a time range, for example BTC versus ETH versus SOL over 30 days
* Visualizing whale or holder distributions for a specific token
* Building a portfolio breakdown by chain or asset
* Tracking wallet activity with charts
* Comparing stock performance across sectors (AAPL, TSLA, NVDA, AMZN, MSFT)
* Turning a research output into a visual you can share

{% hint style="info" %}
Data Visualization queries typically cost more credits than standard Chat responses. The cost scales with the number of assets, the date range, and the number of charts rendered. Start with a table-only request if you want to control credit spend, then add charts in a follow-up.
{% endhint %}

***

## Upload images or files

You can drop the files in the chat box to attach images, Excel/CSV files, or PDFs alongside your question. Minara reads the content and incorporates it into its response, for example analyzing a chart screenshot you annotated, reviewing a trading journal in Excel, or summarizing a whitepaper PDF.

Up to 5 files, 10 MB each. See [Multimodal input](multimodal-input.md) for details and examples.
