# Lighter

\[Lighter]\([https://lighter.xyz/](https://lighter.xyz/)) is a zero-knowledge perpetuals exchange. In Minara, orders placed against a Lighter wallet route to Lighter's on-chain order book.

## Trust model

Lighter is a Layer-2 perpetuals DEX that runs its matching and settlement under a zero-knowledge proof system. Trades are executed on-chain with the same trust model as the underlying chain, not on a custodial exchange backend. Minara does not operate Lighter; it is the interface and execution layer on top.

## Deposit

Lighter wallets accept USDC deposits via Arbitrum. Deposits from other networks or tokens are not credited to the wallet and must be recovered by exporting the wallet's private key.

For step-by-step deposit instructions, see [Deposit](../../guide/managing-funds-and-trading/deposit.md#deposit).

## Trading

Lighter wallets support the same order types, margin modes, and risk controls as Hyperliquid wallets. The available asset list comes from Lighter's listings and appears in the asset selector on the Perps trading page when a Lighter wallet is active.
