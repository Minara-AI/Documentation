# Prediction markets

**Why do all three prediction markets show NO — or all show YES?** This is expected behavior, not a bug.

Each of the three bet types is a separate prediction market. Minara's AI evaluates each one independently, comparing its own probability estimate for the event against how the market has priced that probability. The goal is to find edges — cases where the AI's estimate differs meaningfully from the implied odds.

Whether the AI recommends YES or NO depends on two factors working together:

* **Win rate**: how likely the AI thinks the event is to occur
* **Odds**: how much the market pays out if it does

A high-probability outcome isn't automatically a YES if the odds are too low to justify the bet. The AI recommends YES only when its probability estimate is higher than what the market's price implies.

**How the AI calculates probabilities for a Range market**

For a Range market with three outcomes — Below, In-range, and Above — the AI calls a single model that outputs P(BTC > X), the probability that BTC exceeds a given price at settlement. It runs this calculation for each boundary price.
