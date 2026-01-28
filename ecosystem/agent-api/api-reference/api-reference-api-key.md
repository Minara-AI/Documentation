# API Reference (API Key)

Technical specifications for the Minara Agent API endpoints.

### Developer API

The core endpoint for interacting with Minara's conversational AI.



{% openapi-operation spec="minara-api-v1-1" path="/v1/developer/chat" method="post" %}
[OpenAPI minara-api-v1-1](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/5191c0cc22b2ce42b322a0c755e7201082c55e4d48cc266f0d2973adb99934f5.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260128%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260128T072237Z&X-Amz-Expires=172800&X-Amz-Signature=8adc98e9f8c544a60dc91ed909f0d91fe45ae407e64918b924c3bd77ba5f39bb&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="minara-api-v1-1" path="/v1/developer/intent-to-swap-tx" method="post" %}
[OpenAPI minara-api-v1-1](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/5191c0cc22b2ce42b322a0c755e7201082c55e4d48cc266f0d2973adb99934f5.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260128%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260128T072237Z&X-Amz-Expires=172800&X-Amz-Signature=8adc98e9f8c544a60dc91ed909f0d91fe45ae407e64918b924c3bd77ba5f39bb&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="minara-api-v1-1" path="/v1/developer/perp-trading-suggestion" method="post" %}
[OpenAPI minara-api-v1-1](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/5191c0cc22b2ce42b322a0c755e7201082c55e4d48cc266f0d2973adb99934f5.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260128%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260128T072237Z&X-Amz-Expires=172800&X-Amz-Signature=8adc98e9f8c544a60dc91ed909f0d91fe45ae407e64918b924c3bd77ba5f39bb&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="minara-api-v1-1" path="/v1/developer/prediction-market-ask" method="post" %}
[OpenAPI minara-api-v1-1](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/5191c0cc22b2ce42b322a0c755e7201082c55e4d48cc266f0d2973adb99934f5.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260128%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260128T072237Z&X-Amz-Expires=172800&X-Amz-Signature=8adc98e9f8c544a60dc91ed909f0d91fe45ae407e64918b924c3bd77ba5f39bb&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

## Developer API

## Chat

### Endpoint

`POST https://api.minara.ai/v1/developer/chat`

### Request Body

| Parameter         | Type    | Required | Description                                                             |
| ----------------- | ------- | -------- | ----------------------------------------------------------------------- |
| `chatId`          | string  | No       | Optional. Unique conversation ID to continue an existing chat.          |
| `mode`            | string  | Yes      | Model mode: 'fast' for quick responses, 'expert' for in-depth analysis. |
| `stream`          | boolean | Yes      | Set to true for streaming (SSE), false for standard JSON response.      |
| `message`         | object  | Yes      | Message object with role and content                                    |
| `message.role`    | string  | Yes      | Message sender role, must be 'user'.                                    |
| `message.content` | string  | Yes      | The user's query content.                                               |

### Example Request

```bash
curl -X POST https://api.minara.ai/v1/developer/chat \
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

`POST https://api.minara.ai/v1/developer/intent-to-swap-tx`

Convert natural language trading intent into an executable swap transaction payload. Compatible with OKX DEX by default.

### Request Body

| Parameter       | Type   | Required | Description                                                          |
| --------------- | ------ | -------- | -------------------------------------------------------------------- |
| `intent`        | string | Yes      | Natural language swap intent (e.g., "swap 0.1 ETH to USDC")          |
| `walletAddress` | string | Yes      | User wallet address (0x...)                                          |
| `chain`         | string | No       | Chain name (e.g., "base", "ethereum", "bsc", "arbitrum", "optimism") |

### Example Request

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

### Response

```json
{
  "transaction": {
    "chain": "base",
    "inputTokenAddress": "0x4200000000000000000000000000000000000006",
    "inputTokenSymbol": "ETH",
    "outputTokenAddress": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
    "outputTokenSymbol": "USDC",
    "amount": "0.1",
    "amountPercentage": 100,
    "slippagePercent": "0.5"
  }
}
```

***

## Perpetual Trading Suggestion

### Endpoint

`POST https://api.minara.ai/v1/developer/perp-trading-suggestion`

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
curl -X POST https://api.minara.ai/v1/developer/perp-trading-suggestion \
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

`POST https://api.minara.ai/v1/developer/prediction-market-ask`

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
curl -X POST https://api.minara.ai/v1/developer/prediction-market-ask \
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
