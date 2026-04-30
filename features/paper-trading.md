# Paper Trading

Paper Trading on Minara is a real-time forward test. You run a strategy with virtual capital while the engine applies actual Hyperliquid market data, fee schedule, and funding rate. The result is a high-fidelity preview of what live execution would cost, without any real capital at risk.

***

## What is Paper Trading?

Paper Trading is a deployment mode. The same strategy logic that powers a live deployment runs in `mode = paper`, against a virtual account. The engine pulls Hyperliquid candles, charges real maker and taker fees on every fill, and settles funding rate hourly from the live Hyperliquid funding API. The only thing that is virtual is the capital.

It is **not** a sandbox. It is a forward test.

A backtest answers the question "did this work on history?" Paper Trading answers the question "does this still work, in real time, after the friction the live venue actually charges?" The latter is the question that determines whether a strategy is worth committing real capital to.

***

## Who is Paper Trading for?

| User type | What Paper Trading gives them |
|---|---|
| **Beginners** | A risk-free way to see how a strategy actually behaves on a real venue, before learning the cost of mistakes the hard way. |
| **Traders** | A high-fidelity forward test for validating backtested strategies, comparing parameter variations, and deciding which configurations are worth funding live. |
| **Developers** | A testbed for new strategy logic against real market data, fees, and funding, with full audit logs (trades, fees, funding settlements) preserved on archive. |

***

## How to Access

From any strategy detail page, click the **🧪 Run paper** button next to **🚀 Deploy live**. A configuration dialog opens. Set virtual initial capital (between $100 and $1,000,000) and click **Start paper**.

Active and archived paper runs are visible in two places:
- The strategy detail page, under the **Paper trading history** section, scoped to that strategy.
- The global **My paper trading** list, which shows every paper run across all strategies.

***

## How Paper Trading Works

### Data source

Candles are pulled from **Hyperliquid**, not Binance. This is the key difference between Paper Trading and most retail "paper" tools, and the reason a paper result on Minara is comparable to live execution on Hyperliquid.

When a paper run starts, the engine warms up indicators using up to 5,000 historical Hyperliquid bars (or all available bars if fewer exist). After warmup, the candle polling cadence matches what a live deployment would use for the same interval.

### Fees

Fees are charged at the **real Hyperliquid maker/taker rate**, sourced from a configuration file maintained by engineering and updated when Hyperliquid changes its rate schedule.

| Order type | Rate applied |
|---|---|
| Market order (signal triggers immediate fill) | Taker |
| Limit order (signal posts a passive order) | Maker |

Open and close are charged separately. Each fill writes to a `PaperTrade.fee` field, so every fee is auditable on the archived run.

### Funding rate

Every position open on a paper deployment is settled **every hour** (or at whatever cadence Hyperliquid uses for the asset). The engine pulls the live funding rate from the Hyperliquid API and computes:

```
funding_cost = position.notional × funding_rate
```

Direction:
- **Long position**: `balance -= funding_cost` (pays when rate is positive, receives when negative)
- **Short position**: `balance += funding_cost`

Each settlement writes a row to `funding_log` with timestamp, applied rate, notional, and computed amount. The funding history is exposed in the run detail view.

### Slippage

Slippage is **not modeled** in the current version. The fill engine accepts a `slippage_bps` parameter that defaults to 0. A future release will replace the default with either an order-book-depth-based estimate or a configurable bps assumption.

***

## Run Lifecycle

A paper deployment moves through three states:

| State | Description |
|---|---|
| `running` | Active forward test. Strategy is consuming candles and the engine is executing fills against the virtual account. |
| (no `idle` state) | Paper Trading does not support pause/resume. |
| `archived` | Final state. Read-only. Final snapshot is frozen and the run cannot be resumed. |

### Stopping and archiving

Clicking **Stop** opens a confirmation dialog. Confirming closes any open positions at current market price, freezes the final snapshot, and moves the run to history.

The frozen `final_snapshot` includes:
- Final net PnL, split into fees component and funding component
- Equity curve (full timeseries)
- Complete trade log with per-trade fees
- Complete funding settlement log
- Maximum drawdown, win rate, profit factor, Sharpe ratio
- Total runtime
- Initial configuration (strategy, asset, interval, initial capital)

### Constraints

- **One active paper run per (strategy, asset) pair.** This avoids ambiguity when comparing results.
- **Initial capital is set once.** No mid-run injection. Run a new paper deployment if you want a different account size.
- **No pause and resume.** Stop is always archive.
- **Strategy deletion archives all related runs.** Deleting a strategy auto-archives every active paper deployment associated with it.

***

## Promoting a Paper Run to Live

When a paper run looks promising, the run detail page exposes a **Deploy live** action. The strategy, asset, and interval are pre-filled into the live deployment dialog. The user adds a wallet selection and acknowledges live trading risk. From the user's perspective, the paper-to-live transition is a wallet step, not a re-configuration step.

***

## What Paper Trading Can and Cannot Do

**Can:**
- Apply real Hyperliquid candles, maker/taker fees, and funding rate to a strategy
- Maintain a complete audit trail (trade log, fee log, funding log)
- Calculate the same performance statistics as live deployments (drawdown, win rate, profit factor, Sharpe)
- Carry forward configuration to a live deployment in one click

**Cannot:**
- Model slippage (deferred to v2)
- Accept mid-run capital adjustments
- Pause or resume after stop
- Run multiple paper deployments on the same (strategy, asset) pair simultaneously
- Replay a previously archived run

***

## Tips

- **Run for at least 2 weeks.** A few days is too short for funding rate effects to compound visibly. Two to four weeks is usually enough for the cost structure to express itself.
- **Compare paper PnL to backtest PnL on the same window.** If paper diverges substantially from backtest, the friction (fees + funding + candle source) is the issue, not the alpha. This is a useful diagnostic before deploying live.
- **Use $1M virtual capital to test scaling.** The engine treats notional consistently, so funding cost scales linearly. Worth checking whether the strategy is still positive expectancy at the size you would actually deploy at.
- **Watch the funding log on perp strategies.** For market-neutral or basis strategies, funding is often the dominant line item. The funding history is where you find out.

***

## Disclaimers

Paper Trading uses virtual capital. No real funds are placed at risk during a paper run.

The cost structure modeled in Paper Trading (Hyperliquid fees and funding rate) is sourced from Hyperliquid's published rates and live API. While we apply these rates faithfully, Hyperliquid may change its rate schedule, and live results may differ from paper results due to factors that are not modeled: notably slippage, liquidity at execution time, and partial fills on large orders.

A favorable Paper Trading result does not guarantee a favorable live trading result. Past performance, including in forward testing, does not guarantee future performance. All live deployments place real capital at risk, including the possibility of total loss. Users should not deploy live capital based solely on a Paper Trading result without their own risk assessment.

<!-- source: /Users/rocky/Desktop/paper trading prd.txt · generated: 2026-04-29 -->
