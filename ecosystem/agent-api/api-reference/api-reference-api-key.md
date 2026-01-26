# API Reference (API Key)

Technical specifications for the Minara Agent API endpoints.

### Developer Chat API

The core endpoint for interacting with Minara's conversational AI. Supports both standard and streaming responses.



{% openapi-operation spec="minara-api-v1-1" path="/v1/developer/chat" method="post" %}
[OpenAPI minara-api-v1-1](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/279b1deb3cad6bfe3e992fc2c937cc3b0646acb319de378964a9689c7ddacf66.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260126%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260126T145033Z&X-Amz-Expires=172800&X-Amz-Signature=cc784b9cf88e8901fe405841ac98f20caa9a1ec3adf88f83973b61a6ce93369d&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

### **Requests**

#### **Endpoint**

```
POST https://api.minara.ai/v1/developer/chat
```

#### **Request Body**

| Parameter         | Type    | Required | Description                                                    |
| ----------------- | ------- | -------- | -------------------------------------------------------------- |
| `chatId`          | String  | No       | Unique conversation ID. Include to append to an existing chat. |
| `mode`            | String  | Yes      | Model mode: `fast` or `expert`.                                |
| `stream`          | Boolean | Yes      | `true` for streaming, `false` for single response.             |
| `message`         | Object  | Yes      | The message object.                                            |
| `message.role`    | String  | Yes      | Must be `user`.                                                |
| `message.content` | String  | Yes      | The user's query text.                                         |

#### **Example Request**

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

#### Standard Response (`stream: false`)

Returns a JSON object with the complete response.

```json
{
  "chatId": "chat_abc123",
  "messageId": "msg_def456",
  "content": "SOL is currently trading at $187.50, up 4.2% in the last 24 hours. Based on the 4H chart, it has broken above the key resistance at $185 with strong volume. RSI is at 62, indicating bullish momentum without being overbought. \n\nSuggestion: Consider a long position with entry around $186-188, take profit at $195, and stop loss at $180..."
  "usage": {}
}
```

#### Streaming Response (`stream: true`)

Returns `Content-Type: text/event-stream` using Server-Sent Events (SSE).

```
data: {"chatId":"chat_abc123","messageId":"msg_def456","object":"chat.completion.chunk","choices":[{"index":0,"delta":{"role":"assistant"},"finish_reason":null}]}

data: {"chatId":"chat_abc123","messageId":"msg_def456","object":"chat.completion.chunk","choices":[{"index":0,"delta":{"content":"SOL is currently trading at $187.50, up 4.2% in the last 24 hours.\n"},"finish_reason":null}]}

data: {"chatId":"chat_abc123","messageId":"msg_def456","object":"chat.completion.chunk","choices":[{"index":0,"delta":{"content":"Based on the 4H chart, it has broken above the key resistance at $185 with strong volume.\n"},"finish_reason":null}]}

data: [DONE]
```
