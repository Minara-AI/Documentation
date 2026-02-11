# API Reference (API Key)

Technical specifications for the Minara Agent API endpoints.

### Developer API

The core endpoint for interacting with Minara's conversational AI.

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/chat" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T121504Z&X-Amz-Expires=172800&X-Amz-Signature=d88bf98e44d991872efa9dc16907c0a66c442eb3ec65e38688b939be92748ed3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="11" path="/v1/developer/intent-to-swap-tx" method="post" %}
[OpenAPI 11](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/c70f51222b06a26b8ebc4c008c89b7cedeb3f5ee0973ff93edf591e6165904dc.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T121504Z&X-Amz-Expires=172800&X-Amz-Signature=bcd0029b51d5ee97c2d22b57073b6eaaab81562c12e8f1173878577c45d3ce38&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/perp-trading-suggestion" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T121504Z&X-Amz-Expires=172800&X-Amz-Signature=d88bf98e44d991872efa9dc16907c0a66c442eb3ec65e38688b939be92748ed3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/prediction-market-ask" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T121504Z&X-Amz-Expires=172800&X-Amz-Signature=d88bf98e44d991872efa9dc16907c0a66c442eb3ec65e38688b939be92748ed3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

## Developer API

## Chat

### Endpoint

`POST https://api-developer.minara.ai/v1/developer/chat`

### Request Body

| Parameter         | Type    | Required | Description                                                             |
| ----------------- | ------- | -------- | ----------------------------------------------------------------------- |
| `mode`            | string  | Yes      | Model mode: 'fast' for quick responses, 'expert' for in-depth analysis. |
| `stream`          | boolean | Yes      | Set to true for streaming (SSE), false for standard JSON response.      |
| `message`         | object  | Yes      | Message object with role and content                                    |
| `message.role`    | string  | Yes      | Message sender role, must be 'user'.                                    |
| `message.content` | string  | Yes      | The user's query content.                                               |

### Example Request

```bash
curl -X POST https://api-developer.minara.ai/v1/developer/chat \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "mode": "fast",
    "stream": false,
    "message": {
      "role": "user",
      "content": "Analyze the recent price action of SOL and give me a trading suggestion."
    }
  }'
```

### Responses

#### Standard Response (stream: false)

Returns a JSON object with the complete response.

```json
{
  "chatId": "chat_abc123",
  "messageId": "msg_def456",
  "content": "SOL is currently trading at $187.50, up 4.2% in the last 24 hours. Based on the 4H chart, it has broken above the key resistance at $185 with strong volume. RSI is at 62, indicating bullish momentum without being overbought. \n\nSuggestion: Consider a long position with entry around $186-188, take profit at $195, and stop loss at $180...",
  "usage": {}
}
```

#### Streaming Response (stream: true)

Returns `Content-Type: text/event-stream` using Server-Sent Events (SSE).

```
data: {"chatId":"chat_abc123","messageId":"msg_def456","object":"chat.completion.chunk","choices":[{"index":0,"delta":{"role":"assistant"},"finish_reason":null}]}

data: {"chatId":"chat_abc123","messageId":"msg_def456","object":"chat.completion.chunk","choices":[{"index":0,"delta":{"content":"SOL is currently trading at $187.50, up 4.2% in the last 24 hours.\n"},"finish_reason":null}]}

data: {"chatId":"chat_abc123","messageId":"msg_def456","object":"chat.completion.chunk","choices":[{"index":0,"delta":{"content":"Based on the 4H chart, it has broken above the key resistance at $185 with strong volume.\n"},"finish_reason":null}]}

data: [DONE]
```

***

## Intent to Swap Transaction

### Endpoint

`POST https://api-developer.minara.ai/v1/developer/intent-to-swap-tx`

Convert natural language trading intent into an executable swap transaction payload. Compatible with OKX DEX by default.

### Request Body

| Parameter       | Type   | Required | Description                                                          |
| --------------- | ------ | -------- | -------------------------------------------------------------------- |
| `intent`        | string | Yes      | Natural language swap intent (e.g., "swap 0.1 ETH to USDC")          |
| `walletAddress` | string | Yes      | User wallet address (0x...)                                          |
| `chain`         | string | No       | Chain name (e.g., "base", "ethereum", "bsc", "arbitrum", "optimism") |

### Example Request

```bash
curl -X POST https://api-developer.minara.ai/v1/developer/intent-to-swap-tx \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "intent": "swap 0.1 ETH to USDC",
    "walletAddress": "0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb1",
    "chain": "base"
  }'
```

### Response

```json
{
  "intent": {
    "chain": "base",
    "inputTokenAddress": null,
    "inputTokenSymbol": "ETH",
    "outputTokenAddress": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
    "outputTokenSymbol": "USDC",
    "amount": "100000000000000000",
    "userWalletAddress": "0x42a345F3d379B5060f0C36580bAF22C395B1D462"
  },
  "quote": {
    "fromTokenAmount": "100000000000000000",
    "toTokenAmount": "194058559",
    "estimatedGas": "1338000",
    "priceImpact": "-0.03",
    "tradeFee": "0.0174870969512694"
  },
  "inputToken": {
    "address": "0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE",
    "symbol": "ETH",
    "decimals": "18",
    "unitPrice": "1960.63"
  },
  "outputToken": {
    "address": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
    "symbol": "USDC",
    "decimals": "6",
    "unitPrice": "0.99989"
  },
  "unsignedTx": {
    "chainType": "evm",
    "from": "0x42a345F3d379B5060f0C36580bAF22C395B1D462",
    "to": "0x4409921ae43a39a11d90f7b96cfd0b8093d9fc",
    "data": "0xf2c42696000000000000000000000000000000000000000000000000000000000003479e...",
    "value": "100000000000000000",
    "gas": "1338000",
    "gasPrice": "10943011",
    "maxPriorityFeePerGas": "7301883"
  }
}
```

***

## Perpetual Trading Suggestion

### Endpoint

`POST https://api-developer.minara.ai/v1/developer/perp-trading-suggestion`

Get AI-powered perpetual trading suggestions with long/short recommendations, entry price, stop loss, take profit levels, and confidence score based on comprehensive market analysis.

### Request Body

| Parameter   | Type   | Required | Description                                                  |
| ----------- | ------ | -------- | ------------------------------------------------------------ |
| `symbol`    | string | Yes      | Trading symbol (e.g., "BTC", "ETH", "SOL")                   |
| `style`     | string | No       | Trading style: "scalping", "day-trading", or "swing-trading" |
| `marginUSD` | number | No       | Margin in USD                                                |
| `leverage`  | number | No       | Leverage multiplier (max: 40)                                |
| `strategy`  | string | No       | Strategy type (more strategies coming soon)                  |

### Example Request

```bash
curl -X POST https://api-developer.minara.ai/v1/developer/perp-trading-suggestion \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "symbol": "BTC",
    "style": "day-trading",
    "marginUSD": 1000,
    "leverage": 10,
    "strategy": "max-profit"
  }'
```

### Response

```json
{
  "entryPrice": 98450,
  "side": "long",
  "stopLossPrice": 96200,
  "takeProfitPrice": 102800,
  "confidence": 78,
  "reasons": [
    "BTC broke above key resistance at $97,500 with strong volume",
    "RSI at 62 indicates bullish momentum without being overbought",
    "MACD showing bullish crossover on 4H timeframe",
    "Volume profile shows accumulation at current levels"
  ],
  "risks": [
    "Potential pullback at $100,000 psychological resistance",
    "High volatility expected around upcoming Fed meeting",
    "Funding rates on major exchanges trending higher"
  ]
}
```

***

## Prediction Market Analysis

### Endpoint

`POST https://api-developer.minara.ai/v1/developer/prediction-market-ask`

AI-powered prediction market analysis. Analyze prediction market events and get probability estimates for each outcome with detailed reasoning.

### Request Body

| Parameter      | Type    | Required | Description                                              |
| -------------- | ------- | -------- | -------------------------------------------------------- |
| `link`         | string  | Yes      | Prediction market page link (e.g., Polymarket event URL) |
| `mode`         | string  | Yes      | Chat mode: "fast" or "expert"                            |
| `only_result`  | boolean | No       | Only return prediction probabilities without reasoning   |
| `customPrompt` | string  | No       | Custom instructions to guide the analysis                |

### Example Request

```bash
curl -X POST https://api-developer.minara.ai/v1/developer/prediction-market-ask \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "link": "https://polymarket.com/event/will-there-be-another-us-government-shutdown-by-january-31",
    "mode": "fast",
    "only_result": false,
    "customPrompt": "Focus on recent news and sentiment analysis. Be more conservative in probability estimates."
  }'
```

### Response

```json
{
  "predictions": [
    {
      "outcome": "Donald Trump",
      "yesProb": 0.65,
      "noProb": 0.35
    },
    {
      "outcome": "Kamala Harris",
      "yesProb": 0.3,
      "noProb": 0.7
    }
  ],
  "reasoning": "Based on recent polling data and historical trends, Trump maintains a slight lead in key swing states. However, the race remains highly competitive with significant uncertainty..."
}
```
