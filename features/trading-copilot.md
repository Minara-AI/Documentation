# Trading Copilot

Trading Copilot helps you make fast, structured perpertual trading decisions. You select a market, choose a trading style and strategy, then click **Ask Long / Short** to get an actionable direction plus take-profit and stop-loss levels, with one-click execution while the strategy is valid.

### How-to Guide

The following guide will cover all functionalities needed for using Minara Trading Copilot:

#### 1. Access&#x20;

Trading Copilot is now open to all Minara users. Access Trading Copilot via: copilot.minara.ai

***

### 2. Ask Long / Short (AI Strategy)

**Ask Long / Short** is the core AI strategy feature of Trading Copilot.

<figure><img src="../.gitbook/assets/图片.png" alt=""><figcaption></figcaption></figure>

#### What it does

Trading Copilot analyzes market data and generates a structured trading plan, including:

* Trade direction: **Long / Short / Neutral**
* Suggested entry, take-profit (TP), and stop-loss (SL)
* A brief explanation of the strategy logic

#### Necessary parameters

* **Initial Margin:**
  * Your default amount of intiail margin for quick orders. It does not affect Minara's strategy output.
* **Style**
  * **Scalping:** Very short-term trades. Focusing on 3-minute charts for quick in-and-out for small moves.
  * **Day:** Short-term trades. Focusing on 15-minute charts for short-term in-and-out.
  * **Swing:** Hold positions for days to weeks. Focus on 4-hour chart timeframes to ride short-term trends.
* **Strategy**
  * **Max Gain:** Optimizes for high reward-to-risk setups with strong backtest upside. Fewer trades, bigger moves.
  * **Max Win Rate** _(coming soon):_ Prioritizes high-probability setups with more flexible entry conditions. More trades, higher consistency.

***

### 3. Core Mechanism

#### Underlying Trading Infrastructure

Minara does **not** provide liquidity or act as a counterparty.

* All perpetual trades are executed on **Hyperliquid**
* Pricing, leverage, funding rates, and liquidity are fully provided by Hyperliquid
* Minara acts only as an **AI interface and execution layer**

#### How Trading Copilot Generates Strategies

Trading Copilot analyzes multiple categories of market signals to generate strategy suggestions.\
These signals are evaluated together to assess **trend direction, momentum, risk, and execution feasibility**.

**Market Structure & Price Action**

* Multi-timeframe candlestick data (based on selected trading style)
* Trend direction and volatility structure
* Key price levels and recent range behavior
* Technical indicators such as EMA, RSI, MACD, etc.&#x20;

**Order Book & Liquidity Signals**

* Real-time order book depth
* Bid–ask imbalance
* Recent trade flow and execution pressure

**Derivatives Market Indicators**

* Funding rate history and direction
* Open interest (OI) changes
* Positioning dynamics inferred from derivatives data

**Risk & Volatility Metrics**

* Recent volatility and range expansion
* Distance to invalidation and stop-loss feasibility
* Risk-to-reward structure of potential setups

**Strategy Filtering & Risk Constraints**

Before a strategy is presented, Trading Copilot applies internal filters to reduce low-quality or high-risk setups, including:

* Excluding trades with unfavorable **risk-to-reward ratios**
* Filtering strategies with insufficient stop-loss buffers
* Avoiding setups where risk parameters are structurally invalid

***

### 4. Deposit & Transfer

Before using trading copilot, funds must be transferred to your Minara Perps Wallet.

#### Deposit flow

1. **Deposit funds into your Minar Spot Wallet (Default wallet)**

<figure><img src="../.gitbook/assets/图片 (1).png" alt="" width="375"><figcaption></figcaption></figure>

2. **Transfer funds from Spot Wallet to Perpetual Wallet**

<figure><img src="../.gitbook/assets/图片 (2).png" alt=""><figcaption></figcaption></figure>

3. Start trading perpetual contracts

#### Transfer rules

* Please note that the transfer happens on-chain, network fee applies.
* **Minimum transfer into Perpetual Wallet:** 10 USDT
* **Minimum transfer out of Perpetual Wallet:** more than 1 USDT
  * Hyperliquid charges a **1 USDT fee** on withdrawals from the perpetual wallet

Direct deposits into the Perpetual Wallet are not yet supported.

***

### 5. Quick Order (AI One-Click Execution)

Quick Order allows you to execute AI-generated strategies efficiently.

#### How it works

* Trading Copilot pre-fills a limit order details based on its strategy (entry, take profit, and stop loss)
* User can place the order with one click
* Before confirming, user can adjust the position size by adjusting:
  * Leverage
  * Initial margin

***

### 6. Manual Orders

For advanced users, manual trading is also supported. Minara Trading currently supports two order types: Market orders and Limit orders.

***

### 7. Position Management

Once positions are open, Trading Copilot provides flexible position controls.

#### Available actions

* **Close All Positions**
  * Instantly close all open positions at market price
  * Requires confirmation
* **Manual close**
  * Close individual positions by:
    * Market orders
    * Limit orders

All realized PnL is reflected immediately after execution.

***

### 8. Open Order Management

You can manage pending orders directly from the trading interface.

#### Supported actions

* Cancel individual open orders
* **Cancel All Orders** with one click

***

### 9. Margin Mode

Trading Copilot supports both margin modes provided by Hyperliquid.

#### Margin options

* **Cross Margin**
  * All positions share the same margin balance
* **Isolated Margin**
  * Margin is isolated per position

You can switch margin modes directly in the trading interface.
