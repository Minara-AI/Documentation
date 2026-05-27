# Lighter

Lighter is a zero-knowledge perpetuals exchange Minara supports for perps trading, alongside Hyperliquid. Orders placed against a Lighter wallet route to Lighter's on-chain order book; orders placed against a Hyperliquid wallet route to Hyperliquid. You choose per wallet which exchange to use.

## Trust model

Lighter is a Layer-2 perpetuals DEX that runs its matching and settlement under a zero-knowledge proof system. Trades are executed on-chain with the same trust model as the underlying chain, not on a custodial exchange backend. Minara does not operate Lighter; it is the interface and execution layer on top.

## How Lighter and Hyperliquid compare in Minara

| | Lighter | Hyperliquid |
|---|---|---|
| Deposit asset | USDC via Arbitrum | USDC via Arbitrum |
| Cross-exchange transfer | Supported (USDC, USDH where available) | Supported (USDC, USDH where available) |
| Transfer fee | None on the Lighter side | $1 deducted by Hyperliquid per outgoing transfer |
| Wallet key model | Same as Hyperliquid | Same as Lighter |

Order types, leverage, funding, and liquidations follow each exchange's own rules. See [Order types](../trading-reference/order-types.md), [Margin & leverage](../trading-reference/margin-and-leverage.md), and [Liquidations](../trading-reference/liquidations.md).

## Using Lighter in Minara

1. Create a Lighter wallet from the `Wallet` panel (see [Deposit funds](../guide/managing-funds-and-trading/how-to-deposit-funds.md#deposit-to-perps-wallet)).
2. Deposit USDC via Arbitrum into the Lighter wallet, or transfer from an existing Hyperliquid wallet (see [Perps wallets](../guide/managing-funds-and-trading/perps-wallets.md#transfer-between-lighter-and-hyperliquid)).
3. On the Perps trading page, pick the Lighter wallet in the top-left wallet selector. Orders placed from that wallet execute on Lighter.

Copilot, Autopilot, and Strategy Studio all work with Lighter wallets the same way they work with Hyperliquid wallets. The exchange used is determined by which wallet is selected when you start a session or strategy.
