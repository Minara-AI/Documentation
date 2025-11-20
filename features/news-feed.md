# News Feed

**News Feed** is Minara’s curated information system that aggregates, analyzes, and summarizes high-value finance-related news in real time. See the real time news feed here: [https://minara.ai/app/discover/news](https://minara.ai/app/discover/news)

<figure><img src="../.gitbook/assets/Frame 1948756743.png" alt=""><figcaption></figcaption></figure>



It transforms fragmented information from global media into structured, verifiable insights, enabling users to understand **what happened**, **why it matters**, and **how it impacts the markets**.

The system continuously monitors multiple trusted sources, removes redundant or repetitive reports, and organizes news into events with context, relevance, and traceable updates.

***

### Core Capabilities

<table><thead><tr><th width="262">Capability</th><th>Description</th></tr></thead><tbody><tr><td>Multi-Source Aggregation</td><td>Collects verified news from hundreds of global crypto, finance, and macroeconomic outlets.</td></tr><tr><td>AI Summarization</td><td>Converts multi-source reports into concise, factual summaries (≈5 min read) with structured sections (“What Happened”, “Why It Matters”, “Market Impact”, etc.).</td></tr><tr><td>Event Grouping</td><td>Detects and merges duplicate reports that describe the same incident, and links sequential developments into a continuous event timeline.</td></tr><tr><td>Impact on Assets</td><td>Identifies which assets, tokens, sectors, or projects are directly affected, and classifies them as bullish or bearish, with an explanation section titled <em>Impact on Assets</em> added to the article.</td></tr><tr><td>Scoring &#x26; Prioritization</td><td>Each event receives an internal relevance score based on its importance, scope, expected duration of influence and significance to broader macroeconomic trends.</td></tr><tr><td>“Key Concept” Module</td><td>When an article focuses on a specific project or concept, a <em>Key Concept</em> section is added to briefly introduce it (e.g., “About Bybit”, “About Lightning Network”).</td></tr><tr><td>Follow-Up Interaction</td><td>Users can ask follow-up questions about the news. Pre-generated follow-up questions are also provided for users to easily explore event context, market effects, or implications. </td></tr><tr><td>Source Transparency</td><td>Each summary cites aggregated sources, ensuring verifiability and transparency.</td></tr></tbody></table>

***

### How It Works

#### **Source Aggregation**

Discover News continuously collects information from verified crypto and financial outlets across multiple formats, including RSS feeds, APIs, and platform announcements.

Incoming articles are automatically **normalized**, **timestamped**, and **scored** to ensure only credible and relevant stories enter the analysis pipeline.

> Minara gathers content from more than 20 primary media sources, such as Cointelegraph, Coindesk, Decrypt, BWEnews, and selected announcements from exchanges and projects.

***

#### **Event Generation**

When a new article is ingested, Minara determines whether it should:

* **Merge** with an existing event (if multiple sources report the _same incident_), or
* **Create** a new independent event that may be linked to existing events as related (if the story represents a follow-up, consequence, or reaction to an existing event).

Each event is anchored to the timestamp of its earliest reported article, ensuring chronological consistency.

***

#### **Asset & Sector Mapping**

Minara performs **entity extraction** and **context tagging** to map which cryptos, stocks, projects, or sectors are directly or indirectly affected by each event.

Each identified entity receives a sentiment label:

* 🟢 **Bullish:** positive catalyst or favorable implication.
* 🔴 **Bearish:** negative catalyst or adverse development.

This classification enables users to instantly see how macro events or project-specific incidents propagate across the broader market.

***

#### **Scoring & Prioritization**

Every event is assigned a **composite score** reflecting its relevance and impact:

* **Importance:** magnitude or market sensitivity of the event.
* **Scope:** the breadth of affected entities or sectors.
* **Long-term Impact**: estimated duration of influence.
* **Significance in Macroeconomics:** the extent to which the event affects key macroeconomic indicators or policy expectations.

For Discover News Feed, low-scoring events are filtered out to reduce noise and improve overall content quality.

***

#### **Summarization**

Once event grouping and score filtering are complete, Minara summarizes the combined sources into a **structured report** with distinct sections:

1. **Summary:** a concise overview of the incident.
2. **Sources:** list of all verified sources included.
3. **What Happened:** factual reconstruction of the event.
4. **Why It Matters:** context and implications for the market.
5. **Market Impact:** short-term and structural effects on assets.
6. **Key Concepts:** concise explanation of key terms or entities mentioned.

All text follows a neutral, journalistic tone — avoiding speculation or promotional phrasing.

***

#### **Updates & Revisions**

Event content dynamically evolves as new reports emerge:

* **Breaking Period (0–24h):** frequent refreshes as more outlets cover the story.
* **Stable Period (24h–3d):** new relevant developments are linked as related instead of merged.
* **Archived Period (>3d):** event frozen for historical reference but remains visible.

***

#### **Follow-Up Interaction**

Every event supports user interaction through the **Follow-Up** feature:

* Minara auto-suggests questions relevant to the story (e.g., “How does this affect BTC?”, “Is this connected to regulation?”, “What could happen next?”).
* Users may also input custom questions to explore deeper context under each event.

In the follow-up chat, users can click the title to view the original news directly without leaving the chat.

<figure><img src="../.gitbook/assets/图片 (83).png" alt=""><figcaption></figcaption></figure>

***

### Future Development

The **News Feed** will continue to evolve toward a more intelligent, personalized experience.

Upcoming improvements include:

* **Personalization:** delivering user-tailored insights based on profile data, composite scores, and topic relevance;
* **Topic Filtering:** allowing users to browse and track news by topics such as _DeFi_, _RWA_, _Stablecoins_, _Infrastructure_, and more;

Additional features such as search and flexible feed views will also be introduced soon.\
Stay tuned!
