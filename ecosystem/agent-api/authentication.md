# Authentication

Minara provides two methods for authenticating API requests.

### API Key (Subscription)

The standard method for **Pro** and **Partner** plan users. Include your API key in the `Authorization` header of every request.

**Format:**

```
Authorization: Bearer <YOUR_API_KEY>
```

**Example:**

```bash
curl -H "Authorization: Bearer sk-minara-xxxxxxxx" https://api.minara.ai/v1/developer/chat
```

> **Security:** Treat your API keys like passwords. Never expose them in client-side code or public repositories.

👉 **Learn more:** [getting-started-by-api-key.md](getting-started-by-api-key.md "mention")

### Pay-As-You-Go (x402)

For usage-based access without a subscription, we support the [**x402 protocol**](https://www.x402.org/). Pay for API calls directly using stablecoins like $USDC (no subscription required).

**x402 API URL**:[https://x402.minara.ai](https://x402.minara.ai/)

**Explore our x402 endpoints:** [Minara on x402scan](https://www.x402scan.com/server/66307a3c-aeb9-4508-9531-71eed69bc9b5)

👉 **Learn more:** [getting-started-by-x402.md](getting-started-by-x402.md "mention")
