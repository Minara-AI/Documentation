# Liquidity

Minara routes perpetual trades to two on-chain order books: Lighter and Hyperliquid. Each perps wallet you create is bound to one of the two exchanges. Switching wallets in the trading interface switches which venue your next order executes on.

## Lighter vs. Hyperliquid in Minara

| | Lighter | Hyperliquid |
|---|---|---|
| Architecture | Zero-knowledge Layer 2 | Self-settled Layer 1 (HyperBFT consensus) |
| Settlement | On-chain via zk-proofs | On-chain, one-block finality |
| Deposit asset | USDC via Arbitrum | USDC via Arbitrum |
| Asset categories in Minara | Perpetuals | Perpetuals |
| Cross-exchange transfer | Supported (USDC, USDH where available) | Supported (USDC, USDH where available) |
| Transfer fee | None on the Lighter side | $1 deducted by Hyperliquid per outgoing transfer |
| Wallet key model | Same as Hyperliquid | Same as Lighter |

Order types, leverage, funding, and liquidations follow each exchange's own rules. See [Order types](../../trading-reference/order-types.md), [Margin & leverage](../../trading-reference/margin-and-leverage.md), and [Liquidations](../../trading-reference/liquidations.md).

## Picking a venue

Most users do not need to choose explicitly. By default your account has one wallet on each exchange, and the trading interface lets you swap between them in one click. If you have funds on one side and want to use the other, transfer between them. See [Deposit](../../guide/managing-funds-and-trading/deposit.md#transfer-between-lighter-and-hyperliquid).

For details on each venue, see [Lighter](lighter.md) and [Hyperliquid](hyperliquid.md).

## Where each venue shows up in Minara

Copilot, Autopilot, and Strategy Studio all work with both Lighter and Hyperliquid wallets. The exchange used is determined by which wallet is selected when you start a session, run a backtest, or deploy a strategy.
