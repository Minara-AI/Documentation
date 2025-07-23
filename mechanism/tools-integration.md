# Tools Integration

## Overview

Currently, Minara integrates the following external tools, including various data sources from the financial and crypto sectors, as well as Minara team's private data and knowledge base.

## Date Source

Minara does not rely on web search for actionable insights, **as they're often unreliable.Instead,** Minara opted to integrate various industry data sources through APIs or MCPs, covering the following categories:

* **Finance Data**: transactions, stocks, tokens, DeFi, NFTs, liquidation, project/VC information, etc
* **Audience Data**: entities, holders, smart money, social identities, P\&L, relationships, etc
* **Sentiment Data**: news, X posts and trends, Greed/Fear index, macro signals, policy headlines, etc

These data are sourced from **50+** leading industry data and sentiment providers, including:

<table><thead><tr><th width="213.83203125">Data Source</th><th>Data Usage</th><th>Latency</th></tr></thead><tbody><tr><td>Minara's private database</td><td>On/off chain identity, wallet tags, industry experience and know-how, private metrics and trading strategies.</td><td>Real-time</td></tr><tr><td>Arkham</td><td>Analyzing transactions, capital inflow&#x26;outflow and identifying entities.</td><td>Real-time</td></tr><tr><td>Alchemy / QuickNode</td><td>Data access to multiple blockchains.</td><td>Real-time</td></tr><tr><td>BitQuery/Birdeye</td><td>Fast and accurate DEX trading data streams. </td><td>Real-time</td></tr><tr><td>Listing/delisting Announcement</td><td>Capture the latest token listing and delisting events.</td><td>1 - 5s</td></tr><tr><td>CoinMarketCap/CoinGecko</td><td>Comprehensive token information, market data and advanced metrics.</td><td>Real-time</td></tr><tr><td>CoinGlass / CoinAnk</td><td>Advanced cryptocurrency data analysis and signals.</td><td>Real-time</td></tr><tr><td>DeFiLlama</td><td>Comprehensive DeFi data.</td><td>Real-time</td></tr><tr><td>Glassnode</td><td>Advanced blockchain and market intelligence.</td><td>Real-time</td></tr><tr><td>NFTGo</td><td>Comprehensive NFT data and market insights.</td><td>Real-time</td></tr><tr><td>Token launchpads like Virtuals.io/Pump.Fun/Bonk.fun</td><td>The latest token launch and trading data.</td><td>Real-time</td></tr><tr><td>RootData</td><td>Comprehensive and reliable information on Web3 projects, teams, funding, and news.</td><td>1min</td></tr><tr><td>X</td><td>Social media data.</td><td>Real-time</td></tr><tr><td>Global news</td><td>Capture macro trends and detect sentiment. Applicable to most scenarios.</td><td>10s</td></tr><tr><td>Yahoo Finance/Futubull</td><td>Traditional financial data like public companies, stocks, commodity, options, futures.</td><td>Real-time</td></tr><tr><td>Financialdataset</td><td>Financial statements, stock prices, company news, SEC fillings, crypto data.</td><td>Real-time</td></tr></tbody></table>

## Blockchain Interaction

