# Prediction Markets

Minara's Prediction Markets feature gives you access to Hyperliquid's binary crypto prediction markets through Minara's trading interface. You can trade Yes or No positions on short-term price events — for example, "Will BTC be above $80,354 at 2:00 PM?" — with AI analysis signals displayed alongside your order panel to help inform your decision.

***

## What is Prediction Markets?

Hyperliquid runs on-chain binary prediction contracts under its Outcome market. Each contract asks a single question about a crypto price event. Yes tokens settle at $1.00 if the condition is met; No tokens settle at $1.00 if it is not. The Yes token price represents the market's current implied probability.

Minara integrates these markets into its trading interface, adding an AI analysis layer that shows confidence scores, edge signals, and estimated profit per $100 for each open contract.

**What you can do with Prediction Markets:**

* Browse active Hyperliquid Outcome markets from within Minara
* View AI analysis for each market: confidence level, Edge %, and Est. profit per $100
* Trade Yes or No positions using USDH
* Analyze market price action on a TradingView candlestick chart
* Use quick-fill amounts ($10, $50, $100, $500, $1,000) or enter a custom size
* Ask Minara for reasoning behind any AI signal without leaving the screen

***

## Who is Prediction Markets for?

| User Type | Experience Level | How to Use |
|---|---|---|
| **Beginners** | New to prediction markets | Start with the AI signal panel — review confidence, edge, and Est. profit per $100 before placing any position. Use smaller amounts to learn how odds and slippage work. |
| **Active Traders** | Familiar with perps or binary outcomes | Use AI signals as one input alongside your own price thesis. Review the TradingView chart and order book before sizing. |
| **Quantitative Traders** | Statistical background | Interpret Edge % in the context of your own probability estimate. Compare AI confidence against market-implied probability (Yes price) to identify divergences. |

***

## How to Access

**In-app:** Log in to Minara → click the **Prediction** tab in the top navigation bar.

Direct URL: `prediction.minara.ai`

***

## Understanding the AI Prediction Panel

The left panel on the Prediction screen shows AI analysis for active Hyperliquid Outcome markets. Each card surfaces a market with Minara's AI assessment.

| Field | What it means |
|---|---|
| **Market title** | The binary question (e.g., "BTC above 80354 on May 10 at 2:00 PM?") |
| **Confidence** | AI confidence in its signal — **High** or **Medium** |
| **Direction** | Which side the AI signal favors — **Buy YES** or **Buy NO** |
| **Edge %** | AI's estimate of statistical advantage at current market prices. Positive Edge means the AI sees value on the signaled side; negative means the market price is against the thesis |
| **Est. Profit** | Estimated profit per $100 invested if the position resolves correctly at current odds |
| **Odds** | Current market odds for the signaled side (e.g., 2.04x) |

The AI panel is a decision-support tool. All trading decisions and order submissions are made by you.

> **Note:** Edge % is a model estimate based on price data and current market conditions. It is not a prediction of outcome. Review each card on its own merits before trading.

***

## Reading the Market

The top bar for each selected market displays:

| Field | What it shows |
|---|---|
| **BTC Price / Countdown** | Current BTC spot price and time remaining until settlement |
| **% Chance** | Current market-implied probability of the Yes outcome |
| **Price (Yes)** | Current cost of one Yes share (equals the implied probability) |
| **24h Change** | Price change in the Yes token over the past 24 hours |
| **24h Volume** | Total trading volume across both sides |

The center panel shows a TradingView candlestick chart of the prediction market contract's Yes token price history — not the underlying BTC price. Use this to assess how market sentiment has shifted over the contract's life.

***

## Placing a Trade

{% stepper %}
{% step %}
### Select a Market

Click any card in the AI Prediction panel, or use the market selector dropdown at the top of the chart area to browse all active Hyperliquid Outcome markets.
{% endstep %}

{% step %}
### Choose a Side

In the right panel, select **Buy** or **Sell**, then choose **Yes** or **No**.

| Side | When |
|---|---|
| **Yes** | You believe the price condition will be met at settlement |
| **No** | You believe the price condition will not be met |

Current implied probability for each side is displayed as a percentage (e.g., Yes 49% / No 51%).
{% endstep %}

{% step %}
### Set Your Amount

Enter a USDH amount or use the quick-fill buttons ($10, $50, $100, $500, $1,000).

Review the order details before confirming:

| Field | What it shows |
|---|---|
| **Slippage** | Estimated price impact at your order size |
| **Avg Price** | Expected average fill price per share |
| **Shares** | Number of shares your amount buys at current odds |
| **Potential Return** | Dollar gain if your position resolves correctly |

> **Review before submitting.** Slippage can be significant on lower-volume contracts. Potential Return is calculated at current market odds and may shift before settlement.
{% endstep %}

{% step %}
### Confirm the Order

Click **Buy Yes** or **Buy No** to submit. Trades settle in USDH.

Your open position appears in the **Outcomes** tab at the bottom of the screen.
{% endstep %}
{% endstepper %}

***

## Asking Minara for Analysis

The **Ask Minara** button in the AI Prediction panel opens an AI chat session in the context of prediction markets. You can ask:

* "Why does the AI signal Buy NO on this BTC market?"
* "What's the reasoning behind the Medium confidence rating?"
* "Which open contract has the highest edge right now?"

The AI response draws on the same data as the signal panel — market price, countdown, and the underlying model inputs.

***

## Monitoring Positions

The bottom panel has four tabs:

| Tab | What it shows |
|---|---|
| **Outcomes** | Your active prediction market positions and current marked-to-market value |
| **Open Orders** | Orders submitted but not yet filled |
| **Trade History** | Completed trades with entry price, exit, and PnL |
| **Order History** | All order submissions including cancelled and partial fills |

Settlement is automatic at each contract's expiry time. Winning tokens credit your USDH balance at $1.00 per share. Losing tokens expire at $0.

***

## What Prediction Markets Can and Cannot Do

### What You Can Define

* Which Hyperliquid Outcome market to trade
* Which side to take (Yes or No)
* Position size in USDH
* Whether to follow, partially follow, or ignore AI signals

### What the Platform Controls

* Which markets are displayed in the AI Prediction panel
* AI signal methodology (confidence tiers, Edge % calculation)
* Settlement timing and price — governed by Hyperliquid's Outcome contract rules, not Minara
* Liquidity — order fill depends on depth in the Hyperliquid Outcome market; Minara does not act as a counterparty

### Current Limitations

* Only Hyperliquid Outcome markets are available. Prediction markets on other protocols are not currently supported.
* The AI signal panel covers a curated subset of active markets; not all Hyperliquid Outcome contracts are shown.
* Slippage can be material on lower-volume contracts. Always review the Slippage field before confirming.
* AI signals are based on price and market data only. Macro events, news, or off-chain developments are not factored in.

***

## Tips for Better Trading

1. Check the countdown before entering. Contracts with under 30 minutes to settlement often have thin liquidity and wider slippage.
2. High confidence + positive Edge is the strongest signal combination. Medium confidence calls warrant more caution and independent review.
3. Use the TradingView chart to see how the Yes token has traded during the contract's life. Flat or choppy charts suggest low conviction in the market.
4. The AI panel is one input, not a directive. Cross-check the AI signal against the market's current % Chance and your own price view.
5. Start with smaller amounts ($10–$50) to get familiar with how slippage and odds behave on lower-volume Outcome contracts.
6. Positions are binary — they resolve fully at settlement. There is no partial outcome. Size accordingly.
7. Ensure your USDH balance is sufficient before trading. **Avail USDH** is shown in the right panel.

***

## Disclaimers

* Prediction market positions resolve at binary outcomes. You either receive full payout at $1.00 per winning share or lose the full amount invested in losing shares.
* All prediction market contracts are settled by Hyperliquid's Outcome protocol. Minara does not control settlement prices or outcomes.
* Minara does not act as a counterparty or liquidity provider for prediction market trades.
* AI signals displayed in the Prediction panel are for informational purposes only and do not constitute financial or investment advice.
* Historical win rates and edge percentages are model estimates based on past price data. They are not indicative of future results.
* All trading involves risk. Only trade with funds you can afford to lose.
* You maintain full control of your positions at all times. Minara does not execute trades autonomously on your behalf.

<figure><img src="../.gitbook/assets/prediction-markets-overview.png" alt="Prediction Markets tab showing AI Prediction panel on the left, TradingView chart in the center, and USDH order panel on the right"><figcaption></figcaption></figure>

<!-- source: screenshot UI (Minara app + Hyperliquid Outcome, 2026-05-09) · generated: 2026-05-09 -->
