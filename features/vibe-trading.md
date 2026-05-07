# Vibe Trading

Vibe Trading lets you describe a trading strategy in plain language and have Minara generate the code, run a backtest, and deploy it — without writing a line of code yourself.

It is the natural-language interface to [Strategy Studio](../features/strategy-studio.md), Minara's algorithmic trading environment built on Pine Runtime (a TypeScript DSL).

***

## How it works

**Describe your strategy**

Tell Minara what you want the strategy to do. For example:

> "Buy when the 9-EMA crosses above the 21-EMA on the 1-hour chart. Exit when RSI goes above 70 or price drops 3% from entry."

**Minara generates the code**

Minara translates your description into Pine Runtime code and opens it in Strategy Studio. You can review the logic in the Code tab before proceeding.

**Run the backtest**

Switch to the Metrics tab to run a backtest on historical data. Minara returns total return, drawdown, win rate, profit factor, and Sharpe ratio. The Trades tab shows each individual entry and exit.

**Deploy to Autopilot**

When you are satisfied with the backtest results, deploy the strategy to Autopilot. It will run live under the same execution and risk-control framework as official Minara strategies.

{% embed url="https://drive.google.com/file/d/1JlGUdubEmJFT_wHuA0VBYdY1puiYc_lt/view?usp=sharing" %}

***

## What you can trade

Vibe Trading strategies work with any asset supported in Strategy Studio, including crypto perpetuals and spot markets across the chains Minara supports.

For on-chain spot trades, Minara uses stablecoins like USDC as the base currency. Supported chains: Solana, Ethereum, Base, BNB Chain, Avalanche, Arbitrum, Optimism, Polygon.

***

## Fees

On-chain spot trades incur the following fees:

- **Network fee (required):** paid to blockchain validators to process the transaction; varies by chain, traffic, and gas price
- **Service fee (required):** 0.1%–1%, charged by the DEX for swap routing and execution
- **Bridge fee (optional):** only applies when transferring assets across chains

For more detail on trading mechanics, see the [managing funds and trading guide](../guide/managing-funds-and-trading/).
