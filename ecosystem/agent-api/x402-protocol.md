# x402 Protocol

The x402 protocol (also known as L402) is an emerging standard for API monetization that enables pay-per-use access without requiring a subscription.

<figure><img src="../../.gitbook/assets/Screen Shot 2026-01-21 at 6.10.41 PM.png" alt=""><figcaption></figcaption></figure>

### What is x402?

x402 is a native "pay-to-play" system for the web. Instead of pre-paying for a subscription, you pay for each API call directly using stablecoins like $USDC.

**How it works:**

1. You make an API request to a protected endpoint.
2. The server responds with a "payment required" invoice.
3. You pay the invoice on-chain using a supported stablecoin.
4. You receive a cryptographic proof-of-payment (a "preimage").
5. Include the proof in your next request to access the API.

### Why Use x402?

| Benefit             | Description                                                 |
| ------------------- | ----------------------------------------------------------- |
| **No Subscription** | Pay only for what you use.                                  |
| **Permissionless**  | No account or approval needed to start.                     |
| **Flexible**        | Ideal for experiments, variable usage, or one-off projects. |
| **Programmable**    | Designed for machine-to-machine payments.                   |

### How to Use x402 with Minara

1. **Explore the Endpoint**: Visit our service on [x402scan](https://www.x402scan.com/server/66307a3c-aeb9-4508-9531-71eed69bc9b5).
2. **Generate Invoice**: Request a protected resource to receive a payment invoice.
3. **Pay**: Use a compatible wallet to pay with $USDC.
4. **Authenticate**: Include the invoice and preimage in your request header.

**Header Format:**

```
Authorization: L402 <invoice>:<preimage>
```

For implementation details, explore libraries and tools compatible with the L402/x402 protocol.
