# Prediction Markets

Minara's Prediction Markets feature lets you trade binary crypto price outcomes powered by [Outcome.xyz](https://outcome.xyz), with an AI layer that scans live markets and surfaces opportunities ranked by confidence and statistical edge.

***

## What is Prediction Markets?

Prediction Markets is a trading mode inside Minara where you take Yes or No positions on short-term crypto price events — for example, "Will BTC be below $78,746 at 2:00 PM on May 10?"

**What you can do with Prediction Markets:**

* Browse AI-curated prediction market opportunities with confidence scores (High / Medium) and Edge %
* Review estimated profit per $100 and current odds before placing a trade
* Trade Yes or No positions on binary crypto price outcomes
* Use TradingView charts to analyze market price action for each outcome
* Ask the AI for a direct recommendation on any open market via "Ask Minara"
* Place trades with USDH using quick-fill amounts ($10, $50, $100, $500, $1,000)

***

## Who is Prediction Markets for?

| User Type | Experience Level | How to Use |
|---|---|---|
| **Beginners** | New to prediction markets | Start with the AI Prediction panel — review confidence and Est. Profit per $100 before placing any trade |
| **Active Traders** | Familiar with perps or spot trading | Use the TradingView chart and order book to evaluate market-implied probability vs. AI edge signal |
| **Researchers** | Quantitative background | Interpret Edge % as the AI's signal-to-noise estimate and cross-check against your own price thesis |

***

## How to Access

**In-app:** Log in to Minara → click the **Prediction** tab in the top navigation bar.

Direct URL: `https://minara.ai/app/trade/prediction` _(confirm with team before publishing)_

***

## Reading the AI Prediction Panel

The left panel on the Prediction screen is the AI Prediction feed. It automatically scans live markets on Outcome.xyz and surfaces a ranked list of opportunities.

Each card shows:

| Field | What it means |
|---|---|
| **Market title** | The binary question being traded (e.g., "BTC below 78746 on May 10 at 2:00 PM?") |
| **Confidence** | AI confidence in its call — **High** or **Medium** |
| **Direction** | Which side the AI recommends — **Buy YES** or **Buy NO** |
| **Edge %** | AI's estimated statistical advantage. Positive Edge means the AI sees value; negative Edge means the market price is against the AI's thesis |
| **Est. Profit** | Estimated profit per $100 invested if the AI call is correct |
| **Odds** | Current market odds for the recommended side (e.g., 1.92x) |

The AI updates recommendations as market prices move. A card that showed Edge +2.0% earlier in the session may show a different value as the market reprices.

> **Note:** Edge % is the AI's statistical estimate based on historical price behavior and current market data. It is not a guarantee. Negative Edge trades have appeared in the feed — review each card individually before trading.

***

## Placing a Trade

{% stepper %}
{% step %}
### Select a Market

Click any market card in the AI Prediction panel, or browse markets manually using the market selector dropdown at the top of the chart area.
{% endstep %}

{% step %}
### Review the Market

The center panel loads a TradingView candlestick chart showing historical price action for the prediction market contract (not the underlying asset price).

The top bar shows:
* **BTC Price / Countdown** — current spot price and time remaining until settlement
* **Probability trend** — percentage change in implied probability
* **Price (Yes)** — current cost of a YES share
* **24h Change** and **24h Volume** — market activity metrics
{% endstep %}

{% step %}
### Choose a Side

In the right panel, select **Buy** or **Sell**, then choose **Yes** or **No**.

| Side | When to use |
|---|---|
| **Yes** | You believe the outcome will occur (e.g., BTC will be below the target price at settlement) |
| **No** | You believe the outcome will not occur |

Current implied probability for each side is displayed as a percentage (e.g., Yes 8.1% / No 91.9%).
{% endstep %}

{% step %}
### Set Amount and Review Order Details

Enter your USDH amount manually or use the quick-fill buttons ($10, $50, $100, $500, $1,000).

Before confirming, review:

| Field | What it shows |
|---|---|
| **Slippage** | Estimated price impact of your order size |
| **Avg Price** | Expected average fill price per share |
| **Shares** | Number of shares your USDH buys at current odds |
| **Potential Return** | Dollar gain if your position resolves correctly, shown as amount and percentage |

> **Review the risk disclosure.** Potential Return is calculated at current market odds. Slippage and price movement before settlement can reduce actual returns.
{% endstep %}

{% step %}
### Confirm the Trade

Click **Buy Yes** or **Buy No** to submit the order. Trades settle in USDH.

Your open position appears in the **Outcomes** tab at the bottom of the screen.
{% endstep %}
{% endstepper %}

***

## Asking Minara for a Recommendation

The **Ask Minara** button at the bottom of the AI Prediction panel opens an AI chat session scoped to prediction market context. You can ask questions like:

* "Why is the AI recommending Buy NO on this BTC market?"
* "What's the current probability trend for the May 10 markets?"
* "Which open market has the best risk-adjusted edge right now?"

Minara's AI response is based on the same data powering the prediction panel — current market prices, countdown, and its own confidence model.

***

## Monitoring Open Positions

The bottom panel has four tabs:

| Tab | What it shows |
|---|---|
| **Outcomes** | Your active prediction market positions with current value |
| **Open Orders** | Orders submitted but not yet filled |
| **Trade History** | Completed trades with entry price, exit price, and PnL |
| **Order History** | All order submissions including cancelled and partially filled |

***

## What Prediction Markets Can and Cannot Do

### What You Can Define

* Which market to trade (any market surfaced by the AI or available on Outcome.xyz)
* Direction (Yes or No)
* Amount (in USDH)
* Whether to follow the AI recommendation or override it

### What the Platform Controls

* Which markets are surfaced in the AI Prediction panel (based on Minara's curation model)
* Settlement — all outcomes settle at the expiry time and price defined by Outcome.xyz, not by Minara
* Liquidity — order fill depends on market depth on Outcome.xyz; Minara does not act as a counterparty or provide liquidity

### Current Limitations

* Prediction Markets currently covers **crypto price outcomes only** (BTC-denominated markets)
* Settlement is in USDH; withdrawing proceeds to external wallets follows the standard Minara withdrawal flow
* The AI Prediction panel shows a limited number of curated markets per session; not all Outcome.xyz markets are shown
* Slippage can be significant on low-volume markets — always review the Slippage field before confirming

***

## Tips for Better Trading

1. Check the countdown timer before entering. Markets with under 30 minutes to settlement carry higher price volatility.
2. Positive Edge does not mean guaranteed profit — it means the AI's model sees value at current market prices. Market prices can move against you before settlement.
3. Use the TradingView chart to see how the prediction market has traded historically. A flat candlestick chart suggests low liquidity.
4. High confidence + positive Edge together are the signal the AI is most certain about. Treat Medium confidence calls with more caution.
5. Start with smaller amounts ($10–$50) to understand how slippage and odds work on this market before scaling.
6. "Ask Minara" is useful for understanding the reasoning behind a call, not just the outcome. It can explain what price levels and timeframes the AI used.
7. Your available balance for prediction markets is shown as **Avail USDH** in the right panel. Make sure you have sufficient USDH before trading.

***

## Disclaimers

* Prediction market outcomes are binary — you either receive a payout at settlement or lose your full position. There is no partial result.
* Historical win rates and edge percentages displayed in the AI panel are based on model estimates and past data. They are not indicative of future results.
* Minara does not set settlement prices or control market outcomes. Settlement is governed by Outcome.xyz's protocol.
* All trading involves risk. Only trade with funds you can afford to lose.
* Minara's AI Prediction panel is a tool to assist your research, not financial advice. You are responsible for your own trading decisions.
* You maintain full control of your USDH at all times and can exit open positions subject to available market liquidity.

<figure><img src="../.gitbook/assets/prediction-markets-overview.png" alt="Prediction Markets tab showing AI Prediction panel, TradingView chart, and Buy/Sell order panel"><figcaption></figcaption></figure>

<!-- source: screenshot UI (Minara app, 2026-05-09) · generated: 2026-05-09 -->
