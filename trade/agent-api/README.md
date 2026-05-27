# API

The Minara Agent API gives developers, traders, and market analysts direct access to Minara's financial intelligence and trading execution through a standard HTTP interface.

<figure><img src="../../.gitbook/assets/minara-api.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
API Key access requires a **Pro** plan subscription. On Lite and Starter plans, the API tab in your profile shows an upgrade prompt instead of a key creation interface. Pay-As-You-Go via x402 has no plan requirement.
{% endhint %}

### What you can do with the API

Query live market data across crypto and stocks: wallet activity, DeFi metrics, on-chain flows, alpha signals. All responses are structured for agent consumption.

Send a market context query and get back a long or short recommendation with a preset order payload you can execute immediately. This shortens the loop from signal to trade.

Describe a trade in plain English; the API returns an executable on-chain transaction payload, compatible with OKX DEX by default.

Query AI-estimated probability distributions for event outcomes on prediction markets, backed by market data, news context, and uncertainty bands. Use it to identify mispriced odds and size positions with clearer risk boundaries.

### How it works

Two billing methods:

1. API Key, available on the Pro plan. You generate keys from your Minara profile and include them in the `Authorization` header.
2. Pay-As-You-Go via the [x402 protocol](https://www.x402.org/). Each request is paid with stablecoins like USDC; no plan subscription required.

### Get started

- [Authentication](authentication.md): how requests are authenticated under each billing method.
- [API Key](api-key.md): generate and manage keys on the Pro plan.
- [x402](x402.md): pay per request with stablecoins.
- [API Reference (API Key)](api-reference/api-reference-api-key.md): full endpoint specs for the API Key flow.
- [API Reference (x402)](api-reference/api-reference-x402.md): full endpoint specs for the x402 flow.
