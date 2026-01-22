# Trading Autopilot

Trading Autopilot is Minara’s fully managed mode for perpertual trading.&#x20;

Within the asset scope you authorize, Autopilot can open new positions, take over eligible existing positions, place and maintain stop-loss / take-profit orders, apply trailing risk control, and enforce global safeguards, while keeping all actions observable and reviewable in logs.

### What Autopilot Does

When Autopilot is running, it can perform the following on your behalf, within your authorized trading scope and risk settings:

* Open positions automatically
* Manage positions (including positions you already have, when eligible)
* Place take-profit and stop-loss orders, and update stop-loss as market conditions change
* Reverse positions as market conditions reverses
* Apply global risk controls (e.g., maximum drawdown)
* Exit and notify you when safety conditions are triggered

{% hint style="info" %}
Autopilot is built around three principles:&#x20;

* Every automated action is visible and explainable
* Human can override any time
* Any manual action that conflicts with AI execution is treated as a deliberate override and handled explicitly in-product
{% endhint %}

### How to Access

Path: [**Trade**](https://copilot.minara.ai/) **→ Perps → Autopilot**

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

Copilot Mode
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

Switch to Autopilot
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

Autopilot Turned On
{% endcolumn %}
{% endcolumns %}

* Minara plan subscribers can switch between Copilot and Autopilot mode and run Autopilot. Autopilot is not yet open to free users.
* If user's subscription expires while Autopilot is already running, they can keep viewing and operating the Autopilot panel. However, the user won't be able to start Autopilot without resuming their subscription.

***

### Before you start

**Minimum available funds**

Autopilot requires at least **$50** in available funds (available for Autopilot to trade) to operate.

<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption><p>Real time available funds indicated here</p></figcaption></figure>

{% hint style="info" %}
**Available Funds = Perps Wallet Equity − Occupied Funds**

Occupied Funds = Autopilot margin in use + (if any) worst-case estimated loss of eligible user positions

Worst-case estimated loss is computed from stop-loss trigger (including estimated slippage) plus fees
{% endhint %}

* If there are no open positions in your perps account, In this case, all equity is fully available for Autopilot to allocate into new positions.
* If you hold an existing position, the stop-loss-bounded risk of the existing position is treated as already “reserved,” and only the remaining equity can be used to size new positions.

For now, direct deposit to perps wallet is not yet supported. User will need to deposit **USDC** into their spot wallet, then transfer funds into perps wallet before they start Autopilot.

**Margin mode & position requirements**

Autopilot requires **cross margin** for all managed assets. When Autopilot starts:

* Any isolated margin position blocks starting.
* Any position outside the strategy trading scope blocks starting.

> e.g. If current strategy is only applicable to BTC, ETH, SOL, but the user has an existing position in HYPE, then it would block Autopilot from starting.

***

### Setup Flow

#### First-time enablement

On your first enablement:

1. Autopilot checks eligibility and minimum funds
2. You configure the **Trading Scope** (assets you authorize Autopilot to manage)
3. You confirm risk settings and start Autopilot

> * Within the trading scope, If you already have a cross position on any asset, the asset must be managed by Autopilot and cannot be unselected.
> * All existing open order will be canceled when starting Autopilot.

#### Subsequent enablement

On later enablement attempts, Autopilot reuses your last configuration (scope and risk settings) and starts immediately when funding checks pass. If all assets you previously managed are no longer in the current manageable scope, Autopilot asks you to re-confirm trading scope before starting.

***

### Strategy and Trading scope

Each strategy comes with a preset trading scope that defines the assets to which the strategy applies.

Assets are divided into tiers, which determine leverage limits, margin allocation, and execution priority when multiple entry signals occur simultaneously.

BTC is defined as a tier-1 asset, ETH and SOL are defined as tier-2 assets, and all other assets are assigned lower priority tiers.&#x20;

When multiple assets trigger entry signals at the same time and the account supports fewer concurrent positions than available signals, Autopilot opens positions according to asset priority order.

***

### Position Management

Autopilot places take-profit and stop-loss orders whenever a position is opened, following predefined rules, and trails the stop-loss when conditions allow.

If Autopilot detects rapid changes in technical indicators, it may close the position at market price to reduce losses or protect profits, rather than waiting for the stop-loss order to be triggered.

When conditions are met, Autopilot may close the original position at market price and open a new position in the opposite direction. The size of the new position is calculated using the same logic as other newly opened positions.

***

### Manual Actions

Autopilot treats manual intervention as an intentional override and asks you how to proceed.

#### Removing an asset from management

If you remove an asset from Autopilot scope, Autopilot will not perform further actions on the asset.

However:

* If there is only one managed asset left, it cannot be removed
* If there is an active position on the asset, it cannot be removed.

#### Transferring funds out of Perps Wallet

Transferring funds out of perps wallet will stop Autopilot automatically.

Transferring funds into perps wallet will not stop Autopilot from running; incoming funds increase Autopilot's Available to Trade amount.

#### Manual management on positions

* User may close the positions whenever they want.&#x20;
* User cannot cancel the TP/SL open orders when Autopilot is active.

***

### Safety Exits

Autopilot can stop automatically under the following conditions:

#### Maximum drawdown limit reached

If the user enabled a maximum drawdown limit and it is triggered:

* All Autopilot-managed positions will be closed at market price
* All pending Autopilot orders will be canceled
* Autopilot stops and sends an email notification&#x20;

#### Account equity falls below minimum

If perps account equity is ≤ 5 USDT:

* All Autopilot-managed positions will be closed at market price
* All pending Autopilot orders will be canceled
* Autopilot stops and sends an email notification

### Risk and control notes

Autopilot is built to enforce trading discipline with mandatory TP/SL and trailing stop-loss updates, while leaving you with control over starting, stopping, position management, and the scope you authorize.&#x20;

{% hint style="info" %}
However, please note that perpetual trading involves high risks and Autopilot does not remove market risk nor guarantee profits.
{% endhint %}

