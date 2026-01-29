# Getting Started By xx

## Getting Started By x402

The x402 protocol (also known as L402) is an emerging standard for API monetization that enables pay-per-use access without requiring a subscription.

**Minara x402 endpoint:** `https://x402.minara.ai`

***

### What is x402?

x402 is a native "pay-to-play" system for the web. Instead of pre-paying for a subscription, you pay for each API call directly using stablecoins like $USDC.

**Think of it like a vending machine:**

* You select what you want (make an API request)
* See the price (receive payment instructions)
* Insert coins (pay with USDC)
* Get your item (receive API response)

**Key Benefits:**

✅ **No Subscription Required** - Pay only for what you use\
✅ **Permissionless Access** - No account creation or approval process\
✅ **Instant Activation** - Start using APIs immediately after payment\
✅ **Crypto-Native** - Payments in USDC on Base, Solana, or Polygon\
✅ **Transparent Pricing** - Know exactly what each API call costs

***

### How x402 Works

x402 works in **3 simple steps**:

1️⃣ **Try First** - Make an API request without payment\
2️⃣ **Get the Bill** - Receive payment instructions (amount, chain, recipient)\
3️⃣ **Pay & Access** - Pay with USDC, get proof, retry request, receive response

The entire payment flow happens automatically when you use the x402 SDK.

***

### Quick Start: Using x402 SDK (Recommended)

Most developers use the official x402 SDK which **handles all payment flows automatically**. You just make requests—the SDK handles payment challenges, verification, and settlement for you.

#### Prerequisites

Before you begin, ensure you have:

* ✅ A crypto wallet with USDC (any EVM-compatible wallet)
* ✅ Node.js and npm, Go, or Python and pip
* ✅ Your wallet's private key (for signing payments)

***

#### Step 1: Install Dependencies

<details>

<summary>Node.js / TypeScript</summary>

```bash
# For fetch-based clients (recommended)
npm install @x402/fetch @x402/evm

# For axios-based clients
npm install @x402/axios @x402/evm

# For Solana support, also add:
npm install @x402/svm
```

</details>

<details>

<summary>Python</summary>

```bash
# For httpx (async) - recommended
pip install "x402[httpx]"

# For requests (sync)
pip install "x402[requests]"

# For Solana support, also add:
pip install "x402[svm]"
```

</details>

<details>

<summary>Go</summary>

```bash
go get github.com/coinbase/x402/go
```

</details>

***

#### Step 2: Set Up Your Wallet Signer

<details>

<summary>Node.js (using viem)</summary>

```bash
npm install viem
```

```typescript
import { privateKeyToAccount } from "viem/accounts";

// Create a signer from private key (use environment variable)
const signer = privateKeyToAccount(process.env.EVM_PRIVATE_KEY as `0x${string}`);
```

**For Solana:**

```typescript
import { createKeyPairSignerFromBytes } from "@solana/kit";
import { base58 } from "@scure/base";

const svmSigner = await createKeyPairSignerFromBytes(
  base58.decode(process.env.SOLANA_PRIVATE_KEY!)
);
```

</details>

<details>

<summary>Python (using eth-account)</summary>

```bash
pip install eth_account
```

```python
import os
from eth_account import Account
from x402.mechanisms.evm import EthAccountSigner

account = Account.from_key(os.getenv("EVM_PRIVATE_KEY"))
signer = EthAccountSigner(account)
```

</details>

<details>

<summary>Go</summary>

```go
import (
    evmsigners "github.com/coinbase/x402/go/signers/evm"
)

evmSigner, err := evmsigners.NewClientSignerFromPrivateKey(os.Getenv("EVM_PRIVATE_KEY"))
if err != nil {
    log.Fatal(err)
}
```

</details>

***

#### Step 3: Make Requests - Payments Handled Automatically!

The SDK automatically handles payment challenges for you. Just make requests normally!

<details>

<summary>Node.js (with fetch)</summary>

```typescript
import { wrapFetchWithPayment } from "@x402/fetch";
import { x402Client } from "@x402/core/client";
import { registerExactEvmScheme } from "@x402/evm/exact/client";
import { privateKeyToAccount } from "viem/accounts";

// Create signer
const signer = privateKeyToAccount(process.env.EVM_PRIVATE_KEY as `0x${string}`);

// Create x402 client and register EVM scheme
const client = new x402Client();
registerExactEvmScheme(client, { signer });

// Wrap fetch with payment handling
const fetchWithPayment = wrapFetchWithPayment(fetch, client);

// Make request - payment is handled automatically! 🎉
const response = await fetchWithPayment("https://x402.minara.ai/x402/chat", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    userQuery: "What is the current price of BTC?"
  })
});

const data = await response.json();
console.log("Response:", data.content);

// Get payment receipt (optional)
if (response.ok) {
  const httpClient = new x402HTTPClient(client);
  const paymentResponse = httpClient.getPaymentSettleResponse(
    (name) => response.headers.get(name)
  );
  console.log("Payment settled:", paymentResponse);
}
```

[📖 Full example on GitHub](https://github.com/coinbase/x402/tree/main/examples/typescript/clients/fetch)

</details>

<details>

<summary>Node.js (with axios)</summary>

```typescript
import { x402Client, wrapAxiosWithPayment } from "@x402/axios";
import { registerExactEvmScheme } from "@x402/evm/exact/client";
import { privateKeyToAccount } from "viem/accounts";
import axios from "axios";

// Create signer
const signer = privateKeyToAccount(process.env.EVM_PRIVATE_KEY as `0x${string}`);

// Create x402 client and register EVM scheme
const client = new x402Client();
registerExactEvmScheme(client, { signer });

// Create an Axios instance with payment handling
const api = wrapAxiosWithPayment(
  axios.create({ baseURL: "https://x402.minara.ai" }),
  client
);

// Make request - payment is handled automatically! 🎉
const response = await api.post("/x402/chat", {
  userQuery: "Analyze ETH price action"
});

console.log("Response:", response.data.content);
```

[📖 Full example on GitHub](https://github.com/coinbase/x402/tree/main/examples/typescript/clients/axios)

</details>

<details>

<summary>Python (async with httpx)</summary>

```python
import asyncio
import os
from eth_account import Account

from x402 import x402Client
from x402.http.clients import x402HttpxClient
from x402.mechanisms.evm import EthAccountSigner
from x402.mechanisms.evm.exact.register import register_exact_evm_client


async def call_minara():
    # Create client and register EVM scheme
    client = x402Client()
    account = Account.from_key(os.getenv("EVM_PRIVATE_KEY"))
    register_exact_evm_client(client, EthAccountSigner(account))

    # Make request - payment is handled automatically! 🎉
    async with x402HttpxClient(client) as http:
        response = await http.post(
            "https://x402.minara.ai/x402/chat",
            json={"userQuery": "What is BTC price?"}
        )
        await response.aread()
        
        data = response.json()
        print(f"Response: {data['content']}")


asyncio.run(call_minara())
```

[📖 Full example on GitHub](https://github.com/coinbase/x402/tree/main/examples/python/clients/httpx)

</details>

<details>

<summary>Python (sync with requests)</summary>

```python
import os
from eth_account import Account

from x402 import x402ClientSync
from x402.http.clients import x402_requests
from x402.mechanisms.evm import EthAccountSigner
from x402.mechanisms.evm.exact.register import register_exact_evm_client


def call_minara():
    # Create client and register EVM scheme
    client = x402ClientSync()
    account = Account.from_key(os.getenv("EVM_PRIVATE_KEY"))
    register_exact_evm_client(client, EthAccountSigner(account))

    # Make request - payment is handled automatically! 🎉
    with x402_requests(client) as session:
        response = session.post(
            "https://x402.minara.ai/x402/chat",
            json={"userQuery": "What is BTC price?"}
        )
        
        data = response.json()
        print(f"Response: {data['content']}")


call_minara()
```

[📖 Full example on GitHub](https://github.com/coinbase/x402/tree/main/examples/python/clients/requests)

</details>

<details>

<summary>Go</summary>

```go
package main

import (
    "bytes"
    "context"
    "encoding/json"
    "fmt"
    "net/http"
    "os"
    "time"

    x402 "github.com/coinbase/x402/go"
    x402http "github.com/coinbase/x402/go/http"
    evm "github.com/coinbase/x402/go/mechanisms/evm/exact/client"
    evmsigners "github.com/coinbase/x402/go/signers/evm"
)

func main() {
    // Create EVM signer
    evmSigner, _ := evmsigners.NewClientSignerFromPrivateKey(os.Getenv("EVM_PRIVATE_KEY"))

    // Create x402 client and register EVM scheme
    x402Client := x402.Newx402Client().
        Register("eip155:*", evm.NewExactEvmScheme(evmSigner))

    // Wrap HTTP client with payment handling
    httpClient := x402http.WrapHTTPClientWithPayment(
        http.DefaultClient,
        x402http.Newx402HTTPClient(x402Client),
    )

    // Prepare request body
    reqBody := map[string]string{"userQuery": "What is BTC price?"}
    jsonData, _ := json.Marshal(reqBody)

    // Make request - payment is handled automatically! 🎉
    ctx, cancel := context.WithTimeout(context.Background(), 30*time.Second)
    defer cancel()

    req, _ := http.NewRequestWithContext(ctx, "POST", "https://x402.minara.ai/x402/chat", bytes.NewBuffer(jsonData))
    req.Header.Set("Content-Type", "application/json")
    
    resp, err := httpClient.Do(req)
    if err != nil {
        fmt.Printf("Request failed: %v\n", err)
        return
    }
    defer resp.Body.Close()

    var data map[string]interface{}
    json.NewDecoder(resp.Body).Decode(&data)
    fmt.Printf("Response: %v\n", data["content"])
}
```

[📖 Full example on GitHub](https://github.com/coinbase/x402/tree/main/examples/go/clients/http)

</details>

***

#### Multi-Chain Support (Base + Solana + Polygon)

You can register multiple payment schemes to support all Minara chains:

```typescript
import { wrapFetchWithPayment } from "@x402/fetch";
import { x402Client } from "@x402/core/client";
import { registerExactEvmScheme } from "@x402/evm/exact/client";
import { registerExactSvmScheme } from "@x402/svm/exact/client";
import { privateKeyToAccount } from "viem/accounts";
import { createKeyPairSignerFromBytes } from "@solana/kit";
import { base58 } from "@scure/base";

// Create signers for different chains
const evmSigner = privateKeyToAccount(process.env.EVM_PRIVATE_KEY as `0x${string}`);
const svmSigner = await createKeyPairSignerFromBytes(
  base58.decode(process.env.SOLANA_PRIVATE_KEY!)
);

// Create client with multiple schemes
const client = new x402Client();
registerExactEvmScheme(client, { signer: evmSigner });  // Base + Polygon
registerExactSvmScheme(client, { signer: svmSigner });  // Solana

const fetchWithPayment = wrapFetchWithPayment(fetch, client);

// Now you can call ANY Minara endpoint! 🚀
// Base endpoints
await fetchWithPayment("https://x402.minara.ai/x402/chat", {...});

// Solana endpoints  
await fetchWithPayment("https://x402.minara.ai/x402/solana/chat", {...});

// Polygon endpoints
await fetchWithPayment("https://x402.minara.ai/x402/polygon/chat", {...});
```

***

### Available Endpoints

Visit [Minara on x402scan](https://www.x402scan.com/server/b9dea1bf-cf70-41d5-96b5-b91c924cfa50) to see all available endpoints and real-time pricing.

#### Minara x402 Endpoints

| Endpoint                              | Price | Chain   | Description                      |
| ------------------------------------- | ----- | ------- | -------------------------------- |
| `/x402/chat`                          | $0.20 | Base    | AI chat (fast mode)              |
| `/x402/chat/expert`                   | $1.25 | Base    | AI chat (expert mode)            |
| `/x402/solana/chat`                   | $0.20 | Solana  | AI chat (fast mode)              |
| `/x402/solana/chat/expert`            | $1.25 | Solana  | AI chat (expert mode)            |
| `/x402/polygon/chat`                  | $0.20 | Polygon | AI chat (fast mode)              |
| `/x402/polygon/chat/expert`           | $1.25 | Polygon | AI chat (expert mode)            |
| `/x402/intent-to-swap-tx`             | $0.10 | Base    | Convert text to swap transaction |
| `/x402/perp-trading-suggestion`       | $0.10 | Base    | Get trading suggestions          |
| `/x402/prediction-market-ask`         | $0.20 | Base    | Analyze prediction markets       |
| `/x402/polygon/prediction-market-ask` | $0.20 | Polygon | Analyze prediction markets       |

***

### Complete Example: Chat with Minara

Here's a complete working example that calls Minara's AI chat endpoint:

```typescript
import { wrapFetchWithPayment } from "@x402/fetch";
import { x402Client, x402HTTPClient } from "@x402/core/client";
import { registerExactEvmScheme } from "@x402/evm/exact/client";
import { privateKeyToAccount } from "viem/accounts";

async function chatWithMinara(query: string) {
  // 1. Set up signer
  const signer = privateKeyToAccount(
    process.env.EVM_PRIVATE_KEY as `0x${string}`
  );

  // 2. Create x402 client
  const client = new x402Client();
  registerExactEvmScheme(client, { signer });

  // 3. Wrap fetch
  const fetchWithPayment = wrapFetchWithPayment(fetch, client);

  // 4. Make request - SDK handles payment automatically!
  const response = await fetchWithPayment("https://x402.minara.ai/x402/chat", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ userQuery: query })
  });

  const data = await response.json();
  return data.content;
}

// Usage
const answer = await chatWithMinara("What is the current price of BTC?");
console.log(answer);
// Output: "BTC is currently trading at $98,450. Key support levels..."
```

**What happened behind the scenes:**

1. ✅ SDK made initial request
2. ✅ Received 402 Payment Required
3. ✅ Automatically paid $0.20 USDC on Base
4. ✅ Retried request with payment proof
5. ✅ Got response with AI answer

All automatic! You just called a function. 🎉

***

### Alternative: Manual Payment Flow (Without SDK)

If you prefer not to use the SDK, you can handle payments manually:

#### Step 1: Make Initial Request

```bash
curl -X POST https://x402.minara.ai/x402/chat \
  -H "Content-Type: application/json" \
  -d '{"userQuery": "What is BTC price?"}'
```

#### Step 2: Receive Payment Challenge

```json
{
  "error": "payment_required",
  "message": "Payment required to access this resource",
  "paymentInstructions": {
    "amount": "0.20",
    "currency": "USDC",
    "recipient": "0xCF5815e9063FA0b04Be0Cb5C1DB583eeF9ef5fbB",
    "chain": "base"
  }
}
```

#### Step 3: Pay with Wallet

Use MetaMask, Phantom, or any Web3 wallet to send USDC to the recipient address.

#### Step 4: Retry with Payment Proof

```bash
curl -X POST https://x402.minara.ai/x402/chat \
  -H "x-payment-response: <payment_proof_token>" \
  -H "Content-Type: application/json" \
  -d '{"userQuery": "What is BTC price?"}'
```

#### Step 5: Get Response

```json
{
  "content": "BTC is currently trading at $98,450..."
}
```

***

### Error Handling

When using the SDK, handle errors like this:

```typescript
try {
  const response = await fetchWithPayment(url, options);
  // Success
} catch (error) {
  if (error.message.includes("No scheme registered")) {
    console.error("❌ Network not supported - register the appropriate scheme");
  } else if (error.message.includes("Payment already attempted")) {
    console.error("❌ Payment failed on retry");
  } else if (error.message.includes("Insufficient balance")) {
    console.error("❌ Not enough USDC in wallet");
  } else {
    console.error("❌ Request failed:", error);
  }
}
```

#### Common Errors from Minara API

**402 Payment Required**

```json
{ "error": "payment_required" }
```

→ Normal! SDK will handle this automatically.

**401 Unauthorized**

```json
{ "error": "unauthorized", "message": "Invalid payment response token" }
```

→ Payment proof invalid or expired. SDK will retry.

**400 Bad Request**

```json
{ "error": "bad_request", "message": "Missing required parameter: userQuery" }
```

→ Check your request body has required fields.

***

### Rate Limits

x402 endpoints are rate-limited per wallet address:

* **AI Endpoints**: 60 requests/minute
* **Trading Endpoints**: 30 requests/minute

If you exceed limits:

```json
{
  "error": "rate_limit_exceeded",
  "message": "Too many requests. Please try again in 30 seconds.",
  "retryAfter": 30
}
```

***

### Advanced: Service Discovery

Instead of hardcoding endpoints, use the x402 Bazaar to discover services dynamically:

```typescript
// Discover all x402 services
const response = await fetch(
  "https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources"
);
const services = await response.json();

// Find affordable services
const affordableServices = services.items.filter((item) =>
  item.accepts.some((req) => Number(req.amount) < 100000) // Under $0.10
);

console.log("Available services:", affordableServices);
```

Learn more in the [x402 Bazaar documentation](https://docs.x402.org/extensions/bazaar).

***

### Resources & Support

#### 📚 Official x402 Resources

* [x402 Protocol Documentation](https://docs.x402.org)
* [Quickstart for Buyers](https://docs.x402.org/getting-started/quickstart-for-buyers)
* [x402 GitHub Repository](https://github.com/coinbase/x402)
* [x402 Discord](https://discord.gg/cdp)

#### 📦 NPM Packages

* [@x402/fetch](https://www.npmjs.com/package/@x402/fetch) - Fetch wrapper
* [@x402/axios](https://www.npmjs.com/package/@x402/axios) - Axios interceptor
* [@x402/evm](https://www.npmjs.com/package/@x402/evm) - EVM support (Base, Polygon)
* [@x402/svm](https://www.npmjs.com/package/@x402/svm) - Solana support
* [x402 Python Package](https://pypi.org/project/x402/)

#### 🔍 Minara Specific

* [Minara on x402scan](https://www.x402scan.com/server/b9dea1bf-cf70-41d5-96b5-b91c924cfa50) - View all endpoints
* Minara API Reference (x402) - Full API documentation
* Minara Discord - Community support

***

### FAQ

#### ❓ Do I need to manually handle payments?

**No!** When you use the x402 SDK, all payment flows are handled automatically. You just make requests like normal.

#### ❓ Which SDK should I use?

* **JavaScript/TypeScript**: Use `@x402/fetch` (simpler) or `@x402/axios` (if you prefer axios)
* **Python**: Use `x402[httpx]` (async) or `x402[requests]` (sync)
* **Go**: Use `github.com/coinbase/x402/go`

#### ❓ Is my private key safe?

Yes. Your private key stays **local** and is only used to sign payment transactions. It's never sent to Minara or any server.

#### ❓ Which chain should I use?

* **Base** - Recommended (fast, cheap, \~2 sec confirmation)
* **Solana** - Very fast (\~1 sec) but need SOL for gas
* **Polygon** - Ethereum-compatible, moderate speed

#### ❓ How much USDC do I need?

Start with $5-10 USDC:

* That's 25-50 fast chat requests ($0.20 each)
* Or 50-100 trading endpoint calls ($0.10 each)

#### ❓ Can I use this in production?

Yes! The x402 protocol is production-ready. Many developers use it for:

* Agent applications
* Trading bots
* Research tools
* Automated workflows

***

### Next Steps

🎯 **Try it now**: Copy one of the code examples above and run it\
📖 **Read API Docs**: View all x402 endpoints →\
💬 **Get Help**: Join Discord →\
🔧 **Advanced Usage**: [Explore lifecycle hooks and extensions →](https://docs.x402.org/advanced-concepts/lifecycle-hooks)
