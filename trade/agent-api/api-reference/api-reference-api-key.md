# API Reference (API Key)

Technical specifications for the Minara Agent API endpoints.

### Developer API

The core endpoint for interacting with Minara's conversational AI.

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/chat" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/95c5c8d68c5204967d207a48bbef6717f9f7f80a460806ecebd12bfe521ab8c7.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260714%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260714T073820Z&X-Amz-Expires=172800&X-Amz-Signature=0bfa8ecd38ea2b02f8ede0a336414570f4e4d115bd1ee39b54ae1f4d3daa34c3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/chat/requests/{id}" method="get" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/95c5c8d68c5204967d207a48bbef6717f9f7f80a460806ecebd12bfe521ab8c7.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260714%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260714T073820Z&X-Amz-Expires=172800&X-Amz-Signature=0bfa8ecd38ea2b02f8ede0a336414570f4e4d115bd1ee39b54ae1f4d3daa34c3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="212-2" path="/v1/developer/intent-to-swap-tx" method="post" %}
[OpenAPI 212-2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/e80f64cdd458a0f090cfdb6df35bbf7657541475d3097e5f89ca3600d864321e.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260714%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260714T073820Z&X-Amz-Expires=172800&X-Amz-Signature=5edc4273aa5248b1fff46eeac704272a809c2296eeef510c4a99cc215e5f9fcc&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/perp-trading-suggestion" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/95c5c8d68c5204967d207a48bbef6717f9f7f80a460806ecebd12bfe521ab8c7.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260714%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260714T073820Z&X-Amz-Expires=172800&X-Amz-Signature=0bfa8ecd38ea2b02f8ede0a336414570f4e4d115bd1ee39b54ae1f4d3daa34c3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-reference-api-key" path="/v1/developer/prediction-market-ask" method="post" %}
[OpenAPI api-reference-api-key](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/95c5c8d68c5204967d207a48bbef6717f9f7f80a460806ecebd12bfe521ab8c7.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260714%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260714T073820Z&X-Amz-Expires=172800&X-Amz-Signature=0bfa8ecd38ea2b02f8ede0a336414570f4e4d115bd1ee39b54ae1f4d3daa34c3&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-schemas spec="212-2" schemas="Message,ChatResponse" grouped="true" %}
[OpenAPI 212-2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/e80f64cdd458a0f090cfdb6df35bbf7657541475d3097e5f89ca3600d864321e.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260714%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260714T073820Z&X-Amz-Expires=172800&X-Amz-Signature=5edc4273aa5248b1fff46eeac704272a809c2296eeef510c4a99cc215e5f9fcc&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-schemas %}

## Background Chat & Idempotency

The `chat` endpoint above supports asynchronous execution and idempotent retries via two optional fields: `background` and `requestId`. The request/response shapes are documented in the OpenAPI block above; this section covers the behavioral rules the schema cannot express.

### Background execution

Set `background: true` (only valid with `stream: false`) to have the request accepted immediately (`202 Accepted`) and processed asynchronously. Poll the status endpoint (`GET /v1/developer/chat/requests/{id}`) with the returned `id` (or your `requestId`) until it reaches a terminal state. Combining `background: true` with `stream: true` returns `400 Bad Request`.

### Idempotency with `requestId`

`requestId` is a client-generated key, unique **within a single API key**, that lets you safely retry a request without generating (and being billed for) a duplicate result. It works with sync, stream, and background modes.

* **Same key, same payload** → the existing job is reused. You get back its current status/result instead of a new generation. If it is still running you receive `202 Accepted`; if it has completed you receive `200 OK` with the result.
* **Same key, different payload** → `409 Conflict` (`"requestId was already used with a different request"`).
* **Reusing an expired key** → `409 Conflict` (`"requestId has expired and cannot be reused"`).

For streaming requests carrying a `requestId`, the response includes an `X-Request-Id` header, generation continues even if the client disconnects, and the final result can be retrieved afterwards via the status endpoint.

### Chat request status notes

The status endpoint (`GET /v1/developer/chat/requests/{id}`) accepts either the server-assigned `id` (e.g. `bg_abc123`) or your `requestId`, and must use the same API key that created the job.

* Records are retained for **24 hours** after reaching a terminal state (`expiresAt`), then removed.
* A request lookup that does not exist or has expired returns `404 Not Found`.
* Interrupted or timed-out jobs fail explicitly (they are **not** retried automatically). Failure `code` is one of `processing_error`, `processing_interrupted`, `processing_timeout`. Submit a new request to retry.
