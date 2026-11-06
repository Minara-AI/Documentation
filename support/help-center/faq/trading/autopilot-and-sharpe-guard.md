# Autopilot and Sharpe Guard

**Why did Autopilot use 50% of my capital in a single trade?**

Autopilot strategies allocate capital based on the position size configured in your strategy settings. By default, Sharpe Guard may deploy a large portion of available capital when its signal confidence is high. To limit exposure per trade, adjust the **Max position size** parameter before activating the strategy. If a trade has already executed and the size is larger than expected, you can manually reduce the position from the Trade tab.

**Why is the strategy only opening longs and refusing to short?**

Sharpe Guard determines trade direction based on the current market regime. During a sustained uptrend, the strategy intentionally avoids shorts to prevent trading against momentum — a common source of avoidable drawdown. Once market conditions shift, the strategy resumes opening positions in both directions. This is by design, not a bug.

**Is Sharpe Guard V2 bugged or is this behavior intentional?**

Most behaviors users flag as bugs are intentional changes in how V2 manages risk compared to V1. V2 is more conservative: it holds positions longer, avoids counter-trend entries, and sizes positions more carefully in volatile conditions.

If you're seeing something that doesn't match this — repeated errors, positions that won't close, or trades that seem random — contact support on [Discord](https://discord.com/invite/minaraai) with your account email and the timestamps of the unexpected behavior.

**Why was everyone switched to V2 without notice?**

Sharpe Guard V2 was rolled out automatically because it shows substantially better risk-adjusted performance compared to V1 in both backtesting and live conditions. The migration was designed to be seamless for active users.

We recognize that more advance notice would have been helpful. We're improving how we communicate strategy updates. If you have feedback about the transition, share it in the [Discord](https://discord.com/invite/minaraai) feedback channel.

**Why is the strategy entering at what looks like the top of a candle?**

Sharpe Guard generates signals at candle close. The actual order executes at the open of the following candle, which can appear to be a worse price when viewed on a chart in hindsight. This is standard behavior for signal-on-close strategies and is not slippage or a bug.

During volatile sessions, entry timing may look suboptimal after the fact — this is normal and not specific to V2.

**How does Sharpe Guard V2 decide when to switch direction?**

V2 monitors trend and momentum signals on a rolling basis. When conditions shift from bullish to bearish (or vice versa), the strategy exits the current position and opens in the opposite direction after signal confirmation. A single candle is not enough to trigger a switch — V2 requires sustained confirmation to avoid false reversals in choppy markets. The behavior is deterministic: the same market conditions will always produce the same signal.

**Can I go back to Sharpe Guard V1?**

V1 is no longer available as an active strategy. If you preferred V1's behavior — more frequent entries, shorter hold times, or a different risk profile — you can build a strategy with similar parameters in Strategy Studio, or describe your preferred approach to Minara Copilot for suggestions.

**Is V2 still in testing? Is it production-ready?**

Yes, V2 is production-ready. It completed internal backtesting and a paper-trading phase before the general rollout. As with any algorithmic strategy, historical performance does not guarantee future results. Monitor your open positions and adjust settings as your needs change.

**Why does V2 seem to perform worse on weekends?**

Crypto markets on weekends have lower liquidity and wider spreads, which affects execution quality across all strategies — not just V2. Lower volume can also cause signals to fire on less reliable price action. This is a known characteristic of algorithmic strategies rather than a V2-specific issue.

**I deposited funds to my Perps wallet but Autopilot still shows "insufficient funds." What's wrong?**

This usually happens when your account balance hasn't been fully recognized yet after a deposit. Network latency can cause a short delay between funds arriving and the available balance updating in the Autopilot interface.

Refresh the page and wait a few minutes. In most cases the balance syncs within 15 minutes of the deposit confirming on-chain.

If the issue persists after 10 minutes, reach out in the [Minara Discord](https://discord.com/invite/minaraai) with your wallet address and the transaction hash so the team can investigate directly.

**What is the minimum balance required to start Autopilot?** Autopilot requires at least **$500** in available funds. This applies whether you deploy your own strategy or subscribe to a published strategy from Strategy Market. An individual published strategy may require more than **$500** if its creator set a higher minimum.

**My Autopilot is in a drawdown. Should I turn it off?**

Drawdowns are a normal part of how the strategy works, not a sign it is broken. Autopilot trades on math and predefined rules: it acts when conditions are met and scales back when they aren't, so there will be quiet stretches where it holds or reduces exposure.

Switching off during a drawdown turns a paper loss into a real one, which is the most common way users lose money. If the swings are hard to sit through, reduce your position size instead of turning the strategy off. Results over time depend on compounding and on whether the strategy keeps its edge, and both need a longer horizon to play out.

**Should I add or cut my allocation based on how it has performed lately?**

Short-term performance is a weak reason to size up or down. The common mistake is adding capital after the strategy has run hot and cutting during a drawdown, which is buying high and selling low.

The steadier approach is the opposite: stay invested or add gradually during flat or weak stretches, and trim after a strong run. This is not because a loss must bounce back. A strategy has no intrinsic value that recovers once it looks cheap, and a losing stretch does not guarantee a profitable one next. The point is to avoid chasing highs and panic-selling lows so you stay in long enough for compounding to work.

**Why does the strategy sometimes lose money during extreme volatility?**

In extreme conditions, such as a sharp crash followed by heavy liquidations and repeated rapid dumps and pumps, many technical indicators and price-volume relationships temporarily stop applying. The strategy can see sizable drawdowns in these windows, and it has before during past market shocks.

As market depth and liquidity rebuild, the strategy has historically returned to profit. These drawdowns come from temporary disorder in market structure rather than the strategy failing. We monitor whether the strategy still holds its edge rather than any single week of P\&L.

**Does Minara profit when I lose? Is Minara the counterparty to my trades?**

No. Minara does not run an order book, does not make markets, and never acts as the counterparty to your trades. Every trade routes to an on-chain venue such as Hyperliquid, where it fills against real market participants at market prices.

Minara provides the strategy and its execution. Your gains and losses come from the market, not from Minara, and there is no house betting against you.
