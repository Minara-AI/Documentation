# API Reference (API Key)

Technical specifications for the Minara Agent API endpoints.

### Developer API

The core endpoint for interacting with Minara's conversational AI.

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/chat" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=814ae1a7db8e675d90f7e091bea2203361cc1010a47f78909ec849bd0708da4b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="212-2" path="/v1/developer/intent-to-swap-tx" method="post" %}
[OpenAPI 212-2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/e80f64cdd458a0f090cfdb6df35bbf7657541475d3097e5f89ca3600d864321e.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=818be66221516281c2681f5644cd101211e19b2d44e434719238bd9e24658ff9&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/perp-trading-suggestion" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=814ae1a7db8e675d90f7e091bea2203361cc1010a47f78909ec849bd0708da4b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/prediction-market-ask" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/eb18bd8b738e65d4003fb5f39d9596a51584ae0c65005df4df876639031f6751.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=814ae1a7db8e675d90f7e091bea2203361cc1010a47f78909ec849bd0708da4b&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-schemas spec="212-2" schemas="Message,ChatResponse" grouped="true" %}
[OpenAPI 212-2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/e80f64cdd458a0f090cfdb6df35bbf7657541475d3097e5f89ca3600d864321e.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260211%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260211T164857Z&X-Amz-Expires=172800&X-Amz-Signature=818be66221516281c2681f5644cd101211e19b2d44e434719238bd9e24658ff9&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-schemas %}

## Background Chat & Idempotency

The chat endpoint supports asynchronous execution and idempotent retries via two optional fields: `background` and `requestId`.

### Background execution

Set `background: true` (only valid with `stream: false`) to have the request accepted immediately and processed asynchronously. Poll the [status endpoint](#chat-request-status) with the returned `id` (or your `requestId`) until it reaches a terminal state.

```bash
curl -X POST https://api.minara.ai/v1/developer/chat \
  -H "Authorization: Bearer <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "mode": "expert",
    "stream": false,
    "background": true,
    "requestId": "my-idempotency-key-1",
    "message": {
      "role": "user",
      "content": "Do a deep analysis of the current BTC market structure."
    }
  }'
```

Response — `202 Accepted`:

```json
{
  "id": "bg_abc123",
  "requestId": "my-idempotency-key-1",
  "chatId": "chat_abc123",
  "status": "queued"
}
```

> Combining `background: true` with `stream: true` returns `400 Bad Request`.

### Idempotency with `requestId`

`requestId` is a client-generated key, unique **within a single API key**, that lets you safely retry a request without generating (and being billed for) a duplicate result. It works with sync, stream, and background modes.

- **Same key, same payload** → the existing job is reused. You get back its current status/result instead of a new generation. If it is still running you receive `202 Accepted`; if it has completed you receive `200 OK` with the result.
- **Same key, different payload** → `409 Conflict` (`"requestId was already used with a different request"`).
- **Reusing an expired key** → `409 Conflict` (`"requestId has expired and cannot be reused"`).

Constraints: 1–128 characters, matching `^[A-Za-z0-9._:-]+$` (letters, digits, `.`, `_`, `:`, `-`).

### Chat request status

Retrieve the status and result of any `requestId`-backed request (sync, stream, or background) by either the server-assigned `id` or your `requestId`.

#### Endpoint

`GET https://api.minara.ai/v1/developer/chat/requests/{id}`

`{id}` may be the server `id` (e.g. `bg_abc123`) or your `requestId`. The request must use the same API key that created the job.

```bash
curl https://api.minara.ai/v1/developer/chat/requests/bg_abc123 \
  -H "Authorization: Bearer <YOUR_API_KEY>"
```

#### Response

```json
{
  "id": "bg_abc123",
  "requestId": "my-idempotency-key-1",
  "chatId": "chat_abc123",
  "status": "completed",
  "executionMode": "background",
  "createdAt": "2026-07-14T08:00:00.000Z",
  "startedAt": "2026-07-14T08:00:01.000Z",
  "completedAt": "2026-07-14T08:00:42.000Z",
  "expiresAt": "2026-07-15T08:00:42.000Z",
  "result": {
    "chatId": "chat_abc123",
    "messageId": "msg_def456",
    "content": "...",
    "usage": { "inputTokens": 1240, "outputTokens": 320, "totalTokens": 1560 }
  }
}
```

| Field           | Type   | Description                                                                       |
| --------------- | ------ | --------------------------------------------------------------------------------- |
| `id`            | string | Server-assigned request id.                                                       |
| `requestId`     | string | Your idempotency key, if one was provided.                                        |
| `chatId`        | string | Chat the request belongs to.                                                      |
| `status`        | string | One of `queued`, `in_progress`, `completed`, `failed`.                            |
| `executionMode` | string | One of `sync`, `stream`, `background`.                                            |
| `result`        | object | Present when `status` is `completed`. Same shape as the standard chat response.   |
| `error`         | object | Present when `status` is `failed`; contains `code` and `message`.                 |

**Notes**

- Records are retained for **24 hours** after reaching a terminal state (`expiresAt`), then removed.
- A request lookup that does not exist or has expired returns `404 Not Found`.
- Interrupted or timed-out jobs fail explicitly (they are **not** retried automatically). Failure `code` is one of `processing_error`, `processing_interrupted`, `processing_timeout`. Submit a new request to retry.
