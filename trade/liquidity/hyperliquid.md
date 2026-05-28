# Hyperliquid

Hyperliquid is an on-chain perpetuals and spot exchange running on a purpose-built Layer 1. In Minara, orders placed against a Hyperliquid wallet route to Hyperliquid's on-chain order book.

## Trust model

Hyperliquid is a self-settled Layer 1 blockchain with native on-chain order matching. It uses a custom consensus algorithm called HyperBFT (inspired by HotStuff) with one-block finality. Orders, cancellations, trades, and liquidations execute on-chain rather than on a centralized matching backend. Funds in a Hyperliquid wallet are held on the Hyperliquid chain, not by Minara.

Hyperliquid also exposes HyperEVM, a general-purpose smart contract environment that can interact with its native trading primitives.

## Deposit

Hyperliquid wallets accept USDC deposits via Arbitrum (Hyperliquid's native bridge). Deposits from other networks or tokens are not credited to the wallet.

For step-by-step deposit instructions, see [Deposit](../../guide/managing-funds-and-trading/deposit.md#deposit).

## Transfers

Outgoing transfers from a Hyperliquid wallet incur a $1 fee deducted by Hyperliquid. This applies to transfers to another Minara wallet (including a Lighter wallet) and to withdrawals to an external Arbitrum address.

For transfer instructions, see [Deposit](../../guide/managing-funds-and-trading/deposit.md#transfer-between-lighter-and-hyperliquid).

## Trading

Hyperliquid wallets support the order types, margin modes, and risk controls described in the trading reference. The available asset list comes from Hyperliquid's listings and appears in the asset selector on the Perps trading page when a Hyperliquid wallet is active.

