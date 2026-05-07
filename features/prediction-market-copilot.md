# Prediction Market Copilot

Prediction Market Copilot is Minara's AI-powered signal engine for Hyperliquid HIP-4 binary prediction markets. It analyzes multi-timeframe technical data, estimates the probability that a price condition will be met at settlement, and compares that estimate against the current market-implied probability to identify contracts where the expected value is positive.

**What you can do with Prediction Market Copilot:**

* Get YES, NO, or WAIT signals for all active HIP-4 contracts in one view
* See AI-estimated probability versus market-implied probability side by side, with edge percentage
* Review expected value per dollar risked before committing to a position
* Execute trades directly from the signal card with preset or custom sizes
* Track open prediction market positions through to automatic settlement

***

## What is Prediction Market Copilot?

Hyperliquid HIP-4 defines on-chain binary prediction contracts. Each contract asks a single question about a price event: will asset X be above price Y at time Z? YES tokens settle at $1.00 if the condition is met. NO tokens settle at $1.00 if it is not.

The YES token price represents the market's collective implied probability. YES at 0.65 means the market assigns a 65% chance to the condition being met.

Prediction Market Copilot adds a second probability estimate to this: the AI probability, derived from technical analysis across five timeframes. The gap between the AI probability and the market price — measured in percentage points — is the edge. Positive edge on the YES side signals a YES recommendation. Positive edge on the NO side signals NO. When expected value is negative on both sides, Copilot recommends WAIT.

The core logic is expected value, not direction:

```
EV(YES) = p_AI × (1 − yes_price) − (1 − p_AI) × yes_price
EV(NO) = (1 − p_AI) × yes_price − p_AI × (1 − yes_price)
```

A Copilot signal fires when EV on one side is positive. The signal does not mean "BTC will go up." It means "at the current price, this contract has a positive expected return given the AI's probability estimate."

***

## Who is Prediction Market Copilot For?

| User Type | Experience Level | How to Use |
|---|---|---|
| **Beginners** | New to prediction markets | Follow Copilot signals directly; use $10–$50 preset sizes; read risk notes on each card |
| **Traders** | Familiar with binary outcomes and EV | Use signals as a first filter; review TA reasoning before execution; size by conviction |
| **Developers / Power Users** | Quantitative or automated workflows | Access structured signal output via API; run position sizing logic on raw probability data |

***

## How to Access

Direct URL: `https://minara.ai/app/prediction-markets`

In-app navigation: **Copilot** → **Prediction Markets** tab

A connected Hyperliquid wallet with USDC balance is required for trade execution. Signal viewing requires no balance.

***

## Reading the Signal List

The signal list displays all active HIP-4 contracts. Each row contains:

| Field | Description |
|---|---|
| **Contract** | Asset, target price, and settlement timestamp |
| **Time remaining** | Countdown to settlement |
| **Direction** | YES (green) / NO (red) / WAIT (gray) |
| **Edge** | AI probability minus market-implied probability, in percentage points |
| **Confidence** | HIGH / MEDIUM / LOW, based on EV magnitude |

The list defaults to sorting by edge size descending. Contracts with the highest expected value appear first.

<figure><img src="../../../.gitbook/assets/prediction-market-copilot-list.png" alt="Signal list showing active HIP-4 contracts sorted by edge percentage"><figcaption></figcaption></figure>

***

## Understanding the Signal Card

Tapping any contract in the signal list opens its signal card.

| Section | Content |
|---|---|
| **Direction badge** | YES / NO / WAIT with HIGH / MEDIUM / LOW confidence |
| **Probability comparison** | AI probability vs market-implied probability (YES price) |
| **Edge** | Gap between the two, in percentage points |
| **Expected value** | EV per $1 risked (e.g., "+$0.14") |
| **TA reasoning** | Three data-specific bullets (max 20 words each) |
| **Risk note** | The single most likely factor that could invalidate the call |
| **Execution** | Preset sizes ($10 / $50 / $100 / $500) + custom; win/loss preview updates live |

<figure><img src="../../../.gitbook/assets/prediction-market-copilot-signal-card.png" alt="Signal card showing YES recommendation with AI probability, market price, edge, and expected value"><figcaption></figcaption></figure>

***

## How AI Probability Works

Copilot generates an AI probability estimate through the following pipeline:

**Step 1 — Technical analysis.** For each contract, Copilot reads K-line data across five timeframes: 1m, 5m, 15m, 1h, and 4h. It computes:

| Indicator | Parameters |
|---|---|
| RSI | 14-period |
| MACD | 12 / 26 / 9 |
| Bollinger Bands | 20-period, 2 std dev |
| EMA | 20, 50, 200 |
| ATR | 14-period |
| Support / Resistance | Local swing highs/lows |
| Funding rate | Current Hyperliquid perpetual rate |

**Step 2 — Timeframe weighting.** The timeframe closest to the settlement window carries more weight. A 2-hour contract emphasizes 5m and 15m data. A 24-hour contract emphasizes 1h and 4h.

**Step 3 — Probability output.** The model synthesizes all inputs into a single probability estimate. When signals conflict or the chart is ambiguous, the estimate moves toward 0.50. Copilot does not produce artificially confident numbers.

***

## Expected Value Calculation

| Variable | Definition |
|---|---|
| `p_AI` | AI-estimated probability that the condition is met |
| `yes_price` | Current YES token price (= market-implied probability) |
| `no_price` | 1 − yes_price |

```
EV(YES) = p_AI × (1 − yes_price) − (1 − p_AI) × yes_price
EV(NO) = (1 − p_AI) × yes_price − p_AI × (1 − yes_price)
```

Copilot recommends YES when EV(YES) > 0, NO when EV(NO) > 0. Confidence tiers:

| EV | Confidence |
|---|---|
| > 0.10 (> 10 percentage points of edge) | HIGH |
| 0.02–0.10 | MEDIUM |
| < 0.02 or negative | WAIT |

***

## Hard Rule Overrides

Three scenarios override the EV calculation:

**Short settlement + favorable position.** When settlement is within 30 minutes and BTC is already more than 0.5% above the target price, Copilot recommends YES directly. Reversing a 0.5% gap in under 30 minutes requires sustained selling pressure that is statistically unlikely in most conditions.

**Long settlement + extreme pricing.** When settlement is more than 20 hours away and either YES or NO is priced below 0.40, Copilot recommends the cheap side regardless of directional view. The time window is long enough that extreme initial pricing typically represents mispricing.

**Overpriced outcomes.** When either side is priced above 0.90 with more than one hour remaining, Copilot recommends WAIT. The apparent winner is already priced in, and the remaining edge does not justify the position.

***

## Trade Execution

From the signal card:

1. Confirm the recommended direction (YES or NO button is highlighted).
2. Select a size — $10, $50, $100, $500, or enter a custom amount.
3. Review the win/loss dollar preview.
4. Swipe to confirm. The order routes to Hyperliquid through your connected wallet.

Settlement is automatic at the contract's expiry time. Winning tokens credit your account at $1.00 each. Losing tokens expire at $0.

***

## Position Tracking

The **Positions** tab shows all open prediction market contracts:

| Field | Description |
|---|---|
| Contract | Target price + settlement timestamp |
| Side | YES or NO |
| Size | Number of tokens |
| Current price | Live YES/NO token price |
| Unrealized P&L | Marked-to-market against current price |
| Time remaining | Countdown to settlement |

***

## What Prediction Market Copilot Can and Cannot Do

### What you can define

* Which contract to trade and which side (or follow Copilot's recommendation)
* Position size per contract
* Whether to act on HIGH, MEDIUM, or LOW confidence signals

### What the platform controls

* AI probability estimation methodology and model parameters
* EV calculation formula and confidence tier thresholds
* Hard rule overrides for short/long settlement scenarios
* Settlement execution (automatic at Hyperliquid contract expiry)

### Current limitations

* BTC HIP-4 contracts only at launch. ETH and other assets to follow.
* No integration with scheduled macro data (CPI, FOMC, etc.). The TA pipeline reads price and volume only.
* No cross-contract portfolio optimization. Each signal is evaluated independently.
* AI probability calibration is a live process. Cold-start accuracy is lower than steady-state accuracy. Historical win rates by confidence tier will be published as data accumulates.
* Minimum trade size and market liquidity on HIP-4 contracts may limit execution on very small orders.

***

## Tips for Better Results

1. Check the risk note on every signal card before executing. It names the specific factor most likely to invalidate the call.
2. Prioritize HIGH confidence signals over MEDIUM when capital is limited. Edge magnitude correlates with historical accuracy in well-calibrated models.
3. Avoid placing positions when the time remaining is less than 5 minutes. Liquidity is typically thin near settlement.
4. Track your own win rate by confidence tier and compare against Copilot's displayed accuracy. Divergences are informative.
5. Use WAIT recommendations actively. Sitting out a contract with no edge is the correct decision, not a missed opportunity.
6. Do not size up dramatically on a single contract because the EV looks large. EV is a per-trade statistical expectation, not a single-trade guarantee.
7. Review the multi-timeframe TA summary in the detailed analysis view for contracts where you are near your trade size limit.

***

## Disclaimers

* Historical backtest performance, where displayed, is not indicative of future results.
* All trading involves risk. Only trade with funds you can afford to lose.
* Prediction Market Copilot provides AI-generated signals for informational purposes only. These signals do not constitute financial or investment advice.
* All perpetual and prediction market trades are executed on Hyperliquid. Minara does not act as a counterparty or liquidity provider.
* AI probability estimates are based on technical analysis and may not account for fundamental, macroeconomic, or news-driven events.
* The user maintains full control of all positions at all times. Copilot does not execute trades autonomously.
* Model calibration improves over time. Early accuracy statistics should be treated as preliminary.

<!-- source: https://byterum.feishu.cn/docx/O2lEddemholouRxBmi4cTINvnth · generated: 2026-05-07 -->
