# Deploy and share

## Introduction

When the backtest and paper results hold up, click Deploy. Deploying finalizes the strategy and opens two independent choices: run it live with your own capital, publish it to the marketplace, or both. You can also skip and do either later.

{% embed url="https://www.youtube.com/watch?index=10&list=PLUp1UC8-DLnM&v=M7TYIOX9ZPg" %}

## Run live or publish

The Strategy deployed dialog offers two actions that do not depend on each other:

* Run live. Start real trading. You pick a wallet and confirm the universe, interval, and leverage. Running live and monitoring are covered in Going live.
* Publish to marketplace. Make the strategy public on Top Strategies, where it is eligible for the leaderboard.

Publishing puts no capital at risk. A published strategy is a backtest that others can see, not a live position.

## Publish it

Choose Publish to marketplace and set how it appears:

* Strategy name and Description. What the strategy does, in plain language.
* Style. Tag it as Mean-Reversion, Trend-Following, Swing, Breakout, Arbitrage, Market Making, or Other.
* Open source. Off by default. When on, anyone can view the code and fork it. Existing forks are not affected if you change this later.
* Backtest baseline. Pick which of your backtests to show as the public track record, with its universe, interval, leverage, period, and PnL.

Click Publish. The strategy's visibility switches to Public, while its source stays private unless you turned on open source.

## After you publish

* It appears on Top Strategies, ranked against other strategies by CAGR, return, Sharpe, max drawdown, and trades over its window.
* It shows in the Rising Creators and New Submissions feeds, and on your creator profile, which tracks how many strategies you have published and how many are currently on Top Strategies.
* Other traders can Star it, and Fork it if you made it open source. A fork copies the strategy into their own workspace to build on. Anyone can open the public strategy page to read its full backtest report, including the composition, IC, and quantile returns.

{% hint style="info" %}
Publishing and running live are separate. You can publish a strategy without ever trading it live, and you can run one live while keeping it private. The backtest baseline you pick is what the public sees, so choose the run that represents the strategy honestly.
{% endhint %}
