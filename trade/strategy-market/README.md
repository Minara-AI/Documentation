# Strategy Market

Strategy Market is where traders discover, compare, run, and publish automated trading strategies. It connects strategies built in [Strategy Studio](../strategy-studio/) with traders who want to use them through Autopilot.

You do not need to write code to run a published strategy. You can inspect its creator, description and intended behavior, historical backtest, post-publication record, risk measurements, and trading activity before deciding whether it fits your account.

{% hint style="warning" %}
Published results describe past performance, not future returns. Review drawdown, fees, trade count, measurement window, and live-forward performance before allocating funds.
{% endhint %}

## Two ways to find strategies

Strategy Market has two discovery views:

* **Marketplace** is the searchable catalog. Use it when you want a particular asset, strategy type, risk profile, style, or creator.
* **Top Strategies** is the comparison view. Use it to examine ranked performance, popular creators, and newly published strategies.

Both views lead to the same strategy detail pages. The difference is how you start your search.

## The strategy lifecycle

A strategy moves through the market in four stages:

1. A creator builds and backtests it in Strategy Studio.
2. The creator publishes it with a description, classification, backtest, and visibility settings.
3. Traders discover and evaluate the publication in Marketplace, Top Strategies, or a creator profile.
4. Eligible traders run it from their own wallet through Autopilot. The creator's code remains private unless the publication is marked `Open source`.

## Choose your path

### If you want to run a strategy

1. [Discover strategies](discover-strategies.md) in Marketplace.
2. [Compare Top Strategies](compare-top-strategies.md) to examine ranked performance and the measurement window shown for each strategy.
3. [Evaluate the strategy](evaluate-a-strategy.md), including its backtest and live-forward record.
4. [Check the creator](creators-and-profiles.md).
5. [Run the strategy](run-a-strategy.md) from a funded wallet.

### If you want to publish a strategy

Build and test the trading logic in Strategy Studio, then use [Publish and manage](publish-and-manage.md) to control its market listing, visibility, subscription terms, and creator presentation.

## Strategy Market and Strategy Studio

| Product | Main purpose | Typical actions |
| --- | --- | --- |
| Strategy Studio | Create and test trading logic | Describe, code, backtest, optimize, and deploy a strategy |
| Strategy Market | Discover and distribute published strategies | Compare, inspect, star, run, publish, and manage a listing |

Editing a publication does not change the underlying trading rules. Return to Strategy Studio when the code, signals, asset universe, timeframe, or execution behavior needs to change.
