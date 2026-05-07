---
hidden: true
---

# Benchmark

Benchmark shows the live performance of MINARA's own trading strategies. It is not a feature you configure — it is a transparency dashboard that lets you track how the strategies built and operated by Minara itself are performing in real markets.

Access it at `/app/trade` → **Benchmark** tab.

## What you're looking at

MINARA runs two active strategies:

| Strategy  | Asset  |
| --------- | ------ |
| MINARA V2 | BTC    |
| MINARA V1 | SILVER |

Each strategy has been deployed to live markets and trades using the same Autopilot execution infrastructure available to users.

MINARA V2 trades Bitcoin (BTC) perpetuals on Hyperliquid using a trend-following approach. MINARA V1 trades silver (SILVER) perpetuals. Both strategies trade under real market conditions with real capital.

## Reading the dashboard

**Total account value** — the current equity of the MINARA strategy portfolio, shown in USD and as a percentage change.

**Chart view** — toggle between `$` (absolute P\&L) and `%` (percentage return). Filter by `72h` for recent performance or `All` for the full history.

**Completed trades** — the full trade log: every position opened and closed, with entry price, exit price, and P\&L for each trade.

**AI reasoning** — for each trade, the rationale Minara's AI used to enter or exit the position. This is the same reasoning layer that drives Autopilot for user accounts.

**Positions** — current open positions held by the strategy.

**Readme** — a description of the strategy logic for each version (V1, V2).

## Why it exists

Benchmark serves as proof of work. Before asking users to run Autopilot on their own capital, Minara runs the same strategies with real funds. The results — including losses and drawdowns — are shown unfiltered.

{% hint style="info" %}
MINARA's performance on Benchmark does not predict your Autopilot results. Your strategies, risk settings, leverage, and allocated capital will differ.
{% endhint %}
