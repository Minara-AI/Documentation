# Strategy Marketplace

Strategy Marketplace connects traders who publish strategies with prospective Subscribers who want to discover, evaluate, or run them. These answers cover discovery, performance review, subscriptions, publishing, and creator profit sharing. For the full product guide, see [Strategy Marketplace](https://minara.ai/docs/trade/strategy-market).

**What is the difference between Strategy Marketplace and Strategy Studio?** Strategy Studio is where you create, edit, backtest, and optimize trading logic. Strategy Marketplace is where published strategies can be discovered, compared, subscribed to, and managed.

Changing a Marketplace listing does not change the strategy's trading rules. Open the strategy in Strategy Studio when you need to change its code, signals, market, timeframe, or execution behavior.

**Should I start with Marketplace or Top Strategies?** Use Marketplace when you already know the asset, strategy category, risk profile, style, availability, or creator you want. Its search and filters help narrow the full catalog.

Use Top Strategies when you want to compare ranked strategies, popular creators, and new submissions before opening individual strategy pages. Both views lead to the same detail pages.

**What is the difference between Time-Series and Cross-Sectional strategies?** A Time-Series strategy makes trading decisions for one market based on that market's own history. A Cross-Sectional strategy evaluates a group of assets and ranks or weights them as a portfolio.

Use the `Category` filter to separate the two. The category describes how the strategy makes decisions, not whether it is safer or more profitable.

**Does a high rank on Top Strategies mean Minara recommends the strategy?** No. Top Strategies is a comparison view, not an investment recommendation. A high rank, high return, verified creator, or large subscriber count does not guarantee future performance.

Open the detail page and review maximum drawdown, Sharpe ratio, measurement window, trade count, costs, and live-forward performance before subscribing.

**Does a Conservative risk label guarantee a small drawdown?** No. `Conservative`, `Balanced`, and `Aggressive` are classifications attached to a publication. They help narrow the catalog but do not guarantee a specific loss limit or future risk level.

Check the strategy's measured maximum drawdown, trading history, trading-volume concentration, per-symbol results, and live-forward record before deciding whether it matches your risk tolerance.

**Why did a strategy's ranking change even though the creator did not edit it?** The comparison chart can use a rolling window and refresh as new performance data arrives. A strategy's rank can change when recent gains or losses enter the window, older data leaves it, or other strategies perform differently.

The `Window` shown in the table is the record displayed for that strategy. It is not necessarily the same as the rolling period used by the comparison chart.

**Why can Annualized Return be much higher than Window Return?** `Window Return` is the total result over the displayed measurement period. `Annualized Return` converts the measured pace into a yearly rate.

Annualizing a strong result from a short window can produce a very large number. It does not mean the strategy earned that amount during the displayed window or will earn it over the next year.

**What do Max Drawdown, Sharpe, and Calmar tell me?** `Max Drawdown` is the largest measured peak-to-trough decline in the displayed record. It shows the depth of the worst decline in that record, not a limit on future losses.

`Sharpe Ratio` compares return with overall volatility. `Calmar Ratio` compares annualized return with maximum drawdown. Read both alongside the measurement window and live-forward record rather than treating either ratio as a pass or fail score.

**What is the difference between backtest and live-forward performance?** A backtest applies the strategy rules to historical data. The `Publish moment` marks when the strategy became public. The live-forward segment records how the published version performed on new market data after that point.

Do not treat the backtest and live-forward sections as one continuous live record. A long backtest with little live-forward history still has limited evidence about post-publication performance.

**What should I review before subscribing to a strategy?** Check the following on the strategy detail page:

1. The market or universe the strategy trades.
2. Whether it is time-series or cross-sectional.
3. The backtest window, live-forward period, and number of trades or fills.
4. Total or annualized return together with maximum drawdown.
5. Sharpe and Calmar ratios where available.
6. Fees, commission, funding costs where applicable, and turnover.
7. Per-symbol results and trading-volume concentration for multi-asset strategies.
8. The creator's description and public profile.

See [Evaluate a strategy](https://minara.ai/docs/trade/strategy-market/evaluate-a-strategy) for a complete review order.

**Does a verified creator badge mean the strategy is safe?** No. Verification is a profile-level status. It does not verify future returns, remove market risk, or guarantee that every strategy from the creator will behave similarly.

Review each strategy separately. Strategies from the same creator may trade different markets and carry different drawdown or concentration risk.

**Is the Share value on a strategy card my wallet allocation?** No. `Share` is the creator profit-share rate configured for a subscribable strategy. It is the percentage of a subscriber's strategy profit allocated to the creator.

Your wallet balance, the amount you allocate, and the creator's profit-share rate are separate values. Review the publication's subscription terms before confirming.

**What do Public, Subscribable, and Open source mean?** These settings control how other users can access a publication.

| Setting        | What it allows                                            |
| -------------- | --------------------------------------------------------- |
| `Public`       | Other users can find and view the strategy.               |
| `Subscribable` | Eligible users can subscribe and run the strategy.        |
| `Open source`  | Other users can view and fork the strategy's source code. |

These settings are independent. A strategy can be public and subscribable while its source remains private. The source is visible only when `Open source` is enabled.

**Can I subscribe to a strategy without seeing its code?** Yes. A subscribable strategy can run through Autopilot while its source remains private. Check the creator's description, backtest, live-forward record, risk measurements, costs, and trade analysis before deciding whether the available information is sufficient for you.

**Does starring a strategy or following a creator start trading?** No. The star icon saves a strategy to the `Starred` tab for later review. `Follow` follows the creator profile. Neither action allocates funds, subscribes your wallet, or starts Autopilot.

**What happens when I select Run on a published strategy?** `Run` opens the subscription and deployment flow. Review the selected strategy, wallet, trading venue, market or universe, interval, and allocation settings before confirming.

After deployment, select `View on Perps` to open the live trading view. The strategy then appears in the `Autopilot` tab on your profile.

**What is the minimum amount required to subscribe to a strategy?** A Subscriber must allocate at least **$500** to run a published Strategy Market strategy. Autopilot now uses the same **$500** minimum for strategies you deploy yourself. A creator may set a higher minimum for an individual published strategy, such as **$1,000**, so review the amount shown in the run flow before confirming.

{% hint style="warning" %}
A backtest is not a live guarantee. Execution, liquidity, fees, funding costs, market conditions, and your allocation can change the result.
{% endhint %}

**Why might my result differ from the public strategy record?** The public page reports the shared strategy publication. Your account starts from your own subscription time, allocation, venue, and execution prices.

Two Subscribers can receive different results from the same strategy because they started at different times or traded under different market and execution conditions.

**Where can I monitor a subscribed strategy?** Open your profile and select `Autopilot`. The page shows the strategy's runtime, Total PnL, 30D PnL, Unrealized PnL, open positions, orders, and trade history for your wallet.

The public strategy page and your Autopilot view serve different purposes. Use the public page to assess the publication and your Autopilot view to monitor your own live run.

**My deployed strategy has not opened any trades. How can I tell whether the strategy or the execution engine is the problem?** Compare the live run with a backtest of the same strategy version. For example, if you deployed a strategy three days ago and its logic should normally open trades every day, run another backtest covering those same three days. Use the same market, timeframe, parameters, and other relevant settings as the deployed strategy.

* If the backtest shows trades but the live strategy opened none, the strategy generated signals and the problem is likely in the deployment or order-execution process. Contact Minara Support and include the strategy name, wallet, deployment time, and backtest result so the team can investigate.
* If the backtest also shows no trades, the strategy's entry conditions were not triggered during that period. Review and optimize the strategy logic before redeploying it.

**How do I publish one of my strategies?** Build and backtest the strategy in Strategy Studio first. Then select `Publish my strategies` from Marketplace or Top Strategies, or open your profile and go to `My Strategies`.

The publication editor lets you set the name, description, style, risk profile, visibility, and subscription terms, and review the backtest attached to the publication. Make sure the description and public backtest refer to the same strategy version.

**Does editing a published listing change the strategy logic?** No. The `About`, `Backtest`, and `Visibility` tabs control the Marketplace publication.

Select `Edit in Strategy Studio` when you need to change code, indicators, parameters, market, timeframe, or execution rules. Run a new backtest after changing the strategy logic, then review the publication again before saving.

**How do subscriptions and creator profit sharing work?** When `Subscribable` is enabled, the creator can configure the profit-share rate, minimum and maximum investment amounts, and subscriber limit. The minimum investment cannot be set below the platform floor of **$500**.

Creators can open the strategy's owner view and select `Subscriber Overview` to review subscriber information and available profit-share data. These settings and records belong to the individual strategy publication.

**How do I remove a strategy from Marketplace?** Open the publication editor, select `Visibility`, turn off `Public`, and save. This removes the strategy from public discovery.

Review the strategy's existing subscribers and your own live-run state before unpublishing. Publishing status and a live run in your own wallet are separate.
