# Prediction Markets

Minara's Prediction Markets feature gives you access to Hyperliquid's binary crypto prediction markets through Minara's trading interface. You can trade Yes or No positions on short-term price events — for example, "Will BTC be above $80,354 at 2:00 PM?" — with AI analysis signals displayed alongside your order panel to help inform your decision.

For trading fees, please refer to [trading-fees.md](../trade/trading-fees.md "mention") .

Try it at: [prediction.minara.ai](https://prediction.minara.aihttps/minara.ai/app/trade/prediction)

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

## What is Prediction Markets?

[Hyperliquid](https://app.hyperliquid.xyz/trade) runs on-chain binary prediction contracts under its Outcome market. Each contract asks a single question about a crypto price event. Yes tokens settle at $1.00 if the condition is met; No tokens settle at $1.00 if it is not. The Yes token price represents the market's current implied probability.

Minara integrates these markets into its trading interface, adding an AI analysis layer that shows confidence scores, edge signals, and estimated profit per $100 for each open contract.

**What you can do with Prediction Markets:**

* Browse active Hyperliquid Outcome markets within Minara
* View AI analysis for each market: confidence level, Edge %, and Est. profit per $100
* Trade Yes or No positions using USDH
* Analyze market price action on a TradingView candlestick chart
* Use quick-fill amounts ($10, $50, $100, $500, $1,000) or enter a custom size
* Ask Minara for reasoning behind any AI signal without leaving the screen

***

## Understanding the AI Prediction Panel

The left panel on the Prediction screen shows AI analysis for active Hyperliquid Outcome markets. Each card surfaces a market with Minara's AI assessment.

<table><thead><tr><th width="135.3359375">Field</th><th>What it means</th></tr></thead><tbody><tr><td><strong>Market title</strong></td><td>The binary question (e.g., "BTC above 80354 on May 10 at 2:00 PM?")</td></tr><tr><td><strong>Confidence</strong></td><td>AI confidence in its signal — <strong>High</strong> or <strong>Medium</strong></td></tr><tr><td><strong>Direction</strong></td><td>Which side the AI signal favors — <strong>Buy YES</strong> or <strong>Buy NO</strong></td></tr><tr><td><strong>Edge %</strong></td><td>AI's estimate of statistical advantage at current market prices. Positive Edge means the AI sees value on the signaled side; negative means the market price is against the thesis</td></tr><tr><td><strong>Est. Profit</strong></td><td>Estimated profit per $100 invested if the position resolves correctly at current odds</td></tr><tr><td><strong>Odds</strong></td><td>Current market odds for the signaled side (e.g., 2.04x)</td></tr></tbody></table>

The AI panel is a decision-support tool. All trading decisions and order submissions are made by you.

> **Note:** Edge % is a model estimate based on price data and current market conditions. It is not a prediction of outcome. Review each card on its own merits before trading.

***

## Reading the Market

The top bar for each selected market displays:

<table><thead><tr><th width="237.29296875">Field</th><th>What it shows</th></tr></thead><tbody><tr><td><strong>BTC Price / Countdown</strong></td><td>Current BTC spot price and time remaining until settlement</td></tr><tr><td><strong>% Chance</strong></td><td>Current market-implied probability of the Yes outcome</td></tr><tr><td><strong>Price (Yes)</strong></td><td>Current cost of one Yes share (equals the implied probability)</td></tr><tr><td><strong>24h Change</strong></td><td>Price change in the Yes token over the past 24 hours</td></tr><tr><td><strong>24h Volume</strong></td><td>Total trading volume across both sides</td></tr></tbody></table>

The center panel shows a TradingView candlestick chart of the prediction market contract's Yes token price history — not the underlying BTC price. Use this to assess how market sentiment has shifted over the contract's life.

<figure><img src="../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

***

## Placing a Trade

{% stepper %}
{% step %}
**Select a Market**

Click any card in the AI Prediction panel, or use the market selector dropdown at the top of the chart area to browse all active Hyperliquid Outcome markets.

<figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Ask Minara**

Minara consultancy panel is right at your left and you can click "Ask Minara" to analyze current risks and profits.

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Choose a Side**

In the right panel, select **Buy** or **Sell**, then choose **Yes** or **No**.

<table><thead><tr><th width="110.71875">Side</th><th>When</th></tr></thead><tbody><tr><td><strong>Yes</strong></td><td>You believe the price condition will be met at settlement</td></tr><tr><td><strong>No</strong></td><td>You believe the price condition will not be met</td></tr></tbody></table>

Current implied probability for each side is displayed as a percentage (e.g., Yes 49% / No 51%).

{% hint style="info" %}
You will need sufficient USDH in your wallet before you can trade outcomes.
{% endhint %}

<figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Set Your Amount**

Enter a USDH amount or use the quick-fill buttons ($10, $50, $100, $500, $1,000).

Review the order details before confirming:

<table><thead><tr><th width="198.328125">Field</th><th>What it shows</th></tr></thead><tbody><tr><td><strong>Slippage</strong></td><td>Estimated price impact at your order size</td></tr><tr><td><strong>Avg Price</strong></td><td>Expected average fill price per share</td></tr><tr><td><strong>Shares</strong></td><td>Number of shares your amount buys at current odds</td></tr><tr><td><strong>Potential Return</strong></td><td>Dollar gain if your position resolves correctly</td></tr></tbody></table>

> **Review before submitting.** Slippage can be significant on lower-volume contracts. Potential Return is calculated at current market odds and may shift before settlement.

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Confirm the Order**

Click **Buy Yes** or **Buy No** to submit. Trades settle in USDH.

Your open position appears in the **Outcomes** tab at the bottom of the screen.
{% endstep %}
{% endstepper %}

## Monitoring Positions

The bottom panel has four tabs:

<table><thead><tr><th width="161.51953125">Tab</th><th>What it shows</th></tr></thead><tbody><tr><td><strong>Outcomes</strong></td><td>Your active prediction market positions and current marked-to-market value</td></tr><tr><td><strong>Open Orders</strong></td><td>Orders submitted but not yet filled</td></tr><tr><td><strong>Trade History</strong></td><td>Completed trades with entry price, exit, and PnL</td></tr><tr><td><strong>Order History</strong></td><td>All order submissions including cancelled and partial fills</td></tr></tbody></table>

Settlement is automatic at each contract's expiry time. Winning tokens credit your USDH balance at $1.00 per share. Losing tokens expire at $0.

## Limitations

* Only Hyperliquid Outcome markets are available. Prediction markets on other protocols are not currently supported.
* The AI signal panel covers a curated subset of active markets; not all Hyperliquid Outcome contracts are shown.
* Slippage can be material on lower-volume contracts. Always review the Slippage field before confirming.
* AI signals are based on price and market data only. Macro events, news, or off-chain developments are not factored in.

## Disclaimers

* Prediction market positions resolve at binary outcomes. You either receive full payout at $1.00 per winning share or lose the full amount invested in losing shares.
* All prediction market contracts are settled by Hyperliquid's Outcome protocol. Minara does not control settlement prices or outcomes.
* Minara does not act as a counterparty or liquidity provider for prediction market trades.
* AI signals displayed in the Prediction panel are for informational purposes only and do not constitute financial or investment advice.
* Historical win rates and edge percentages are model estimates based on past price data. They are not indicative of future results.
* All trading involves risk. Only trade with funds you can afford to lose.
* You maintain full control of your positions at all times. Minara does not execute trades autonomously on your behalf.
