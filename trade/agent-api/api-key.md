# API Key

The API Key method is available to **Pro** and **Partner** plan users. Generate keys from your Minara profile and include them in the `Authorization` header of every request.

***

## Requirements

The Minara Agent API is available exclusively to Pro and Partner plan subscribers. If you are on a free plan, navigate to the **API** tab in your profile to see the upgrade prompt.

If you downgrade your subscription, all active API keys are automatically paused and resume when you renew.

***

## Creating an API key

1. Go to your **Account Profile** at [minara.ai](https://minara.ai).
2. Select the **API Key** tab from the left menu and click **Create**.

<figure><img src="../../.gitbook/assets/Screen Shot 2026-01-26 at 10.42.53 PM.png" alt="API Key tab in Minara account profile showing Create button"><figcaption></figcaption></figure>

3. Enter a name and description to identify the key's usage.

<figure><img src="../../.gitbook/assets/Screen Shot 2026-01-26 at 10.36.10 PM-creat-api-key.png" alt="Create API key dialog with name and description fields"><figcaption></figcaption></figure>

4. Once created, your API key is displayed. Copy and store it securely — it will not be shown again.

<figure><img src="../../.gitbook/assets/Screen Shot 2026-01-26 at 10.36.28 PM.png" alt="Newly created API key displayed for copying"><figcaption></figcaption></figure>

***

## Managing API keys

| Action | Details |
| --- | --- |
| **View keys** | Keys are listed with only the last 4 characters visible. Click to reveal the full key. |
| **Key limit** | Up to 5 API keys per Pro/Partner account. |
| **Delete key** | Requires 2FA confirmation. Deletion is permanent. |

***

## Authentication

Include your API key in the `Authorization` header of every request:

```
Authorization: Bearer <YOUR_API_KEY>
```

**Example:**

```bash
curl -H "Authorization: Bearer sk-minara-xxxxxxxx" \
  https://api.minara.ai/v1/developer/chat
```

{% hint style="warning" %}
Treat your API keys like passwords. Never expose them in client-side code or public repositories.
{% endhint %}

***

## Billing

All API calls consume **credits** from your Minara account. If credits run out, API requests pause until replenished.

***

## API reference

Base URL: `https://api.minara.ai`

### Chat

**`POST /v1/developer/chat`**

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/chat" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=814ae1a7db8e675d90f7e091bea2203361cc1010a47f78909ec849bd0708da4b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `mode` | string | Yes | `fast` for quick responses, `expert` for in-depth analysis |
| `stream` | boolean | Yes | `true` for SSE streaming, `false` for standard JSON |
| `message.role` | string | Yes | Must be `user` |
| `message.content` | string | Yes | The query content |

**Example:**

```bash
curl -X POST https://api.minara.ai/v1/developer/chat \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "mode": "fast",
    "stream": false,
    "message": { "role": "user", "content": "Analyze the recent price action of SOL." }
  }'
```

***

### Intent to swap transaction

**`POST /v1/developer/intent-to-swap-tx`**

{% openapi-operation spec="212-2" path="/v1/developer/intent-to-swap-tx" method="post" %}
[OpenAPI 212-2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/e80f64cdd458a0f090cfdb6df35bbf7657541475d3097e5f89ca3600d864321e.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=818be66221516281c2681f5644cd101211e19b2d44e434719238bd9e24658ff9&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

Convert natural language trading intent into an executable swap transaction payload, compatible with OKX DEX by default.

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `intent` | string | Yes | Natural language swap intent (e.g., "swap 0.1 ETH to USDC") |
| `walletAddress` | string | Yes | User wallet address (0x...) |
| `chain` | string | No | Chain name (e.g., "base", "ethereum", "arbitrum") |

**Example:**

```bash
curl -X POST https://api.minara.ai/v1/developer/intent-to-swap-tx \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "intent": "swap 0.1 ETH to USDC",
    "walletAddress": "0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb1",
    "chain": "base"
  }'
```

***

### Perpetual trading suggestion

**`POST /v1/developer/perp-trading-suggestion`**

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/perp-trading-suggestion" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=814ae1a7db8e675d90f7e091bea2203361cc1010a47f78909ec849bd0708da4b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

Get AI-powered perpetual trading suggestions with long/short recommendations, entry, stop loss, take profit, and confidence score.

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `symbol` | string | Yes | Trading symbol (e.g., "BTC", "ETH", "SOL") |
| `style` | string | No | `scalping`, `day-trading`, or `swing-trading` |
| `marginUSD` | number | No | Margin in USD |
| `leverage` | number | No | Leverage multiplier (max: 40) |
| `strategy` | string | No | Strategy type |

**Example:**

```bash
curl -X POST https://api.minara.ai/v1/developer/perp-trading-suggestion \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "symbol": "BTC",
    "style": "day-trading",
    "marginUSD": 1000,
    "leverage": 10
  }'
```

***

### Prediction market analysis

**`POST /v1/developer/prediction-market-ask`**

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/prediction-market-ask" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=814ae1a7db8e675d90f7e091bea2203361cc1010a47f78909ec849bd0708da4b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

AI-powered probability estimates for prediction market outcomes.

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `link` | string | Yes | Prediction market event URL (e.g., Polymarket) |
| `mode` | string | Yes | `fast` or `expert` |
| `only_result` | boolean | No | Return probabilities only, without reasoning |
| `customPrompt` | string | No | Custom instructions to guide the analysis |

**Example:**

```bash
curl -X POST https://api.minara.ai/v1/developer/prediction-market-ask \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "link": "https://polymarket.com/event/example",
    "mode": "fast"
  }'
```
