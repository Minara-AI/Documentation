# Tools Integration

## Overview

Currently, Minara integrates the following external tools, including various data sources from the financial and crypto sectors, as well as Minara team's private data and knowledge base.

## Date Source

Minara does not rely on web search for actionable insights, **as they're often unreliable.** Instead, Minara opted to integrate various industry data sources, covering the following categories:

* **Finance Data**: transactions, stocks, tokens, DeFi, NFTs, liquidation, project/VC information, etc
* **Audience Data**: entities, holders, smart money, social identities, P\&L, relationships, etc
* **Sentiment Data**: news, X posts and trends, Greed/Fear index, macro signals, policy headlines, etc

These data are sourced from **50+** leading industry data and sentiment providers, including:

<table><thead><tr><th width="238.9375">Data Source</th><th>Data Usage</th><th>Latency</th></tr></thead><tbody><tr><td>Minara's private database</td><td>On/off chain identity, wallet tags, industry experience and know-how, private metrics and trading strategies.</td><td>Real-time</td></tr><tr><td>Arkham</td><td>Analyzing transactions, capital inflow&#x26;outflow and identifying entities.</td><td>Real-time</td></tr><tr><td>Blockchain RPC providers</td><td>Data access to multiple blockchains.</td><td>Real-time</td></tr><tr><td>Listing/delisting Announcement</td><td>Capture the latest token listing and delisting events.</td><td>1 - 3s</td></tr><tr><td>CoinMarketCap/CoinGecko</td><td>Comprehensive token information, price data and advanced metrics.</td><td>Real-time</td></tr><tr><td>CoinGlass</td><td>Advanced cryptocurrency and ETF data &#x26; signals.</td><td>Real-time</td></tr><tr><td>DeFiLlama</td><td>Comprehensive DeFi data.</td><td>Real-time</td></tr><tr><td>Glassnode</td><td>Advanced blockchain and market intelligence.</td><td>Real-time</td></tr><tr><td>NFTGo</td><td>Comprehensive NFT data and market insights.</td><td>Real-time</td></tr><tr><td>Token launchpads like Virtuals.io/Pump.Fun/Bonk.fun</td><td>The latest token launch and trading data.</td><td>Real-time</td></tr><tr><td>RootData</td><td>Comprehensive and reliable information on Web3 projects, teams, funding, and news.</td><td>1min</td></tr><tr><td>Social media</td><td>Social media and sentiment data.</td><td>Real-time</td></tr><tr><td>Global news</td><td>Capture macro trends and detect sentiment. Applicable to most scenarios.</td><td>10s</td></tr><tr><td>Polymarket</td><td>Event prediction and probability</td><td>Real-time</td></tr><tr><td>Goplus</td><td>Token and smart contract security, and risk analysis.</td><td>Real-time</td></tr><tr><td>xStocks</td><td>Tokenized representations of real-world stocks and ETFs.</td><td>Real-time</td></tr><tr><td>OpenAI/Grok Websearch</td><td>Web page search and scraper.</td><td>Real-time</td></tr></tbody></table>

## Blockchain Interaction

| Tool             | Usage                                                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Wallet operation | Send transactions using the user’s smart wallet: trade crypto assets, stake, interact with contracts, and create tokens. |
| N8N workflow     | Create any kinds of crypto workflow by prompting.                                                                        |

