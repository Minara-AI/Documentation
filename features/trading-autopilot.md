# Trading Autopilot

Autopilot executes trading strategies on your behalf, 24 hours a day. Once you select a strategy and define your trading scope, the AI opens positions, manages take-profit and stop-loss orders, trails stops as conditions change, and closes or reverses positions when signals shift, without requiring manual input.

You can override or stop Autopilot at any time.

{% hint style="info" %}
Autopilot is built around three principles:

- Every automated action is visible and explainable
- You can override at any time
- Manual actions that conflict with AI execution are handled explicitly in-product
{% endhint %}

{% hint style="danger" %}
**Autopilot runs leveraged perpetual trades on your behalf.** Mandatory TP/SL and drawdown safety exits reduce but do not eliminate the risk of loss. Positions can still be liquidated in fast or gapping markets. Only allocate funds you can afford to lose. See [Liquidations](../trading-reference/liquidations.md).
{% endhint %}

***

## How to access Autopilot

Path: [Trade](https://copilot.minara.ai/) > Perps > Autopilot

{% columns %}
{% column %}
![](<../.gitbook/assets/image (70).png>)

Copilot Mode
{% endcolumn %}

{% column %}
![](<../.gitbook/assets/image (73).png>)Click Autopilot Tab
{% endcolumn %}

{% column %}
![](<../.gitbook/assets/image (74).png>)Start Autopilot
{% endcolumn %}
{% endcolumns %}

Autopilot is available on paid plans. If your subscription expires while Autopilot is running, you can continue viewing and operating the panel, but you cannot start a new Autopilot session until your subscription is reactivated.

***

## Available strategies

### Sharpe Guard 2.0

Type: Trend-following (15-minute chart)

A trend-following strategy optimized for Sharpe Ratio. It combines fast stop-loss execution, multi-layer trend confirmation, and trailing exits to improve consistency and control drawdowns.

Version 2.0 adds a **market regime detection** layer that classifies prevailing market conditions (trending vs. ranging, risk-on vs. risk-off) and adjusts entry sizing and exit behavior accordingly. This reduces whipsaws in choppy markets and increases conviction during clear trend conditions.

Read more: [Sharpe Guard 2.0 announcement](https://x.com/minara/status/2030132735910785335)

### Classic Futures Grid

Type: Range-bound

A long/short grid strategy for sideways markets. Autopilot suggests grid parameters (grid amount, funding, upper and lower bounds) based on current market data. Once started, the grid engine places and manages orders automatically.

Futures Grid cannot run when there are open positions in the wallet. All existing open orders are canceled on start.

### Supertrend Monitor (legacy — deprecated)

{% hint style="info" %}
Supertrend Monitor has been retired. Existing users should migrate to Sharpe Guard 2.0, which supersedes it with broader regime-aware logic. This section is kept for historical reference only.
{% endhint %}

### Custom strategies from Strategy Studio

Autopilot also supports custom strategies built in [Strategy Studio](strategy-studio.md). Once you deploy a strategy from Studio, it appears in the Autopilot strategy list alongside official strategies and runs under the same execution and risk-control framework.

***

## Trading scope

When you start Autopilot, you define which assets it is authorized to manage. The strategy supports crypto perpetuals such as Bitcoin (BTC), Ethereum (ETH), and Solana (SOL), as well as commodity perpetuals including gold (XAU) and silver. Stock perpetuals such as Apple (AAPL), Tesla (TSLA), and NVIDIA (NVDA) can also be included depending on the active strategy.

Autopilot only opens positions within your authorized scope. Assets outside that scope are not touched.

***

## What Autopilot does automatically

For standard AI strategies (Sharpe Guard 2.0):

- Uses all available funds in your Perps Wallet, including any funds you deposit while Autopilot is running
- Opens positions when entry signals fire within your authorized trading scope
- Places take-profit and stop-loss orders on every position
- Trails the stop-loss as the market moves in your favor
- Closes the position at market price if technical indicators shift rapidly
- Reverses the position when conditions warrant, sizing the new position using the same rules as any new entry
- Applies global risk controls, including maximum drawdown limits
- Exits and sends you a notification if safety thresholds are triggered

***

## Wallet setup

**Minimum funds required**

Autopilot requires at least **$100** in available funds to operate. For Futures Grid, the minimum is calculated dynamically based on the grid parameters.

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption><p>Real-time available funds shown here</p></figcaption></figure>

{% hint style="info" %}
**Available funds = Perps Wallet equity − occupied funds**

Occupied funds = Autopilot margin in use + worst-case estimated loss of any eligible user positions (calculated from stop-loss trigger price, including estimated slippage and fees)
{% endhint %}

If you have no open positions, all equity is available. If you hold an existing position, the stop-loss-bounded risk of that position is reserved, and only the remaining equity is available for new Autopilot positions.

**Depositing funds**

Deposit USDC on Arbitrum directly into the Perps Wallet. Other chains and assets are not supported. Minimum deposit: 10 USDC (after gas fees).

{% hint style="info" %}
If you deposit less than 10 USDC (for example, 5 USDC), the funds remain pending until your cumulative deposits reach 10 USDC or more. At that point, the full amount is credited to the Perps Wallet.
{% endhint %}

**Margin mode requirements**

Autopilot requires cross margin for all managed assets. Autopilot cannot start if:

- You have any isolated margin position, or
- You hold a position outside the strategy's trading scope

For example: if the active strategy covers BTC, ETH, and SOL, but you hold an open HYPE position, you must close HYPE before starting Autopilot.

***

## Starting Autopilot

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

On first enablement:

1. Autopilot checks eligibility and minimum available funds
2. You configure the **Trading Scope**: the assets you authorize Autopilot to manage
3. You confirm risk settings and start

On later enablement attempts, Autopilot reuses your last configuration.

When multiple assets trigger entry signals simultaneously and the account supports fewer concurrent positions than available signals, Autopilot opens positions in asset priority order.

All existing open orders are canceled when Autopilot starts.

***

## Manual actions and overrides

Autopilot treats manual intervention as an intentional override and prompts you on how to proceed.

**Transferring funds out of Perps Wallet**: stops Autopilot automatically.

**Transferring funds into Perps Wallet**: does not stop Autopilot; increases available funds.

**Closing positions manually**: you can close any position at any time.

**TP/SL orders**: you cannot cancel Autopilot-managed TP/SL orders while Autopilot is active.

***

## Safety exits

Autopilot stops automatically under two conditions:

**Initial equity drawdown limit reached** (if you enabled this setting): all managed positions are closed at market price, all pending orders are canceled, Autopilot stops, and you receive an email notification.

**Account equity falls to $5 or below**: same result. Positions are closed, orders are canceled, Autopilot stops, and an email is sent.

***

## Risk note

{% hint style="info" %}
Perpetual trading involves significant market risk. Autopilot enforces trading discipline through mandatory TP/SL and trailing stop-loss management, but it does not eliminate market risk and does not guarantee profits.
{% endhint %}
