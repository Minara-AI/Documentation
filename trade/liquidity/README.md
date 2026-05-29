# Liquidity

Minara routes perpetual trades to two on-chain order books: Lighter and Hyperliquid. Each perps wallet you create is bound to one of the two exchanges. Switching wallets in the trading interface switches which venue your next order executes on.

## Lighter vs. Hyperliquid in Minara

<table><thead><tr><th></th><th width="249">Lighter</th><th>Hyperliquid</th></tr></thead><tbody><tr><td>Architecture</td><td>Zero-knowledge Layer 2</td><td>Self-settled Layer 1 (HyperBFT consensus)</td></tr><tr><td>Settlement</td><td>On-chain via zk-proofs</td><td>On-chain, one-block finality</td></tr><tr><td>Deposit asset</td><td>USDC via Arbitrum</td><td>USDC via Arbitrum</td></tr><tr><td>Asset categories in Minara</td><td>Perpetuals</td><td>Perpetuals</td></tr><tr><td>Cross-exchange transfer</td><td>Supported (USDC, USDH where available)</td><td>Supported (USDC, USDH where available)</td></tr><tr><td>Transfer within the exchange</td><td>$3 deducted by Lighter per transfer (from one Lighter wallet to another)</td><td>$1 deducted by Hyperliquid for new wallets (the first transfer initiated). No fee for subsequent transfers of the same wallet.</td></tr><tr><td>Withdrawal fee</td><td>$3 deducted by Lighter per outgoing transfer (withdrawal)</td><td>$1 deducted by Hyperliquid per outgoing transfer (withdrawal)</td></tr><tr><td>Wallet key model</td><td>StarkEx-derived account model</td><td>EVM-native account model</td></tr></tbody></table>

Order types, leverage, funding, and liquidations follow each exchange's own rules. See [Order types](../../trading-reference/order-types.md), [Margin & leverage](../../trading-reference/margin-and-leverage.md), and [Liquidations](../../trading-reference/liquidations.md).

## Picking a venue

Most users do not need to choose explicitly. By default your account has one wallet on each exchange, and the trading interface lets you swap between them in one click. If you have funds on one side and want to use the other, transfer between them. See [Deposit](../../guide/managing-funds-and-trading/deposit.md#transfer-between-lighter-and-hyperliquid).

For details on each venue, see [Lighter](lighter.md) and [Hyperliquid](hyperliquid.md).

## Where each venue shows up in Minara

Copilot, Autopilot, and Strategy Studio all work with both Lighter and Hyperliquid wallets. The exchange used is determined by which wallet is selected when you start a session, run a backtest, or deploy a strategy.
