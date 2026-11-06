# Your first cross-sectional strategy

A cross-sectional strategy trades a basket of assets by ranking them against each other. Instead of timing one chart, it scores every asset in a universe with one or more factors, holds the top of the ranking long and the bottom short, and rebalances on a schedule. The long and short legs roughly balance, so much of the market's up-or-down move cancels between them.&#x20;

→ [https://minara.ai/app/xstrategy](https://minara.ai/app/xstrategy)

{% embed url="https://www.youtube.com/watch?index=7&list=PLUp1UC8-DLnM&v=H9ARc7gY_OI" %}

## Choose a universe

Switch the toggle above the prompt box to Cross-sectional, then pick a universe. The universe is the pool of assets your strategy ranks and picks from.

| Universe  | What it covers               |
| --------- | ---------------------------- |
| TradFi 30 | 30 traditional-finance names |
| Coin 30   | 29 crypto assets             |
| Coin 50   | 49 crypto assets             |

## Pick the factors

A factor is a rule that turns each asset into a score, applied the same way to every asset so they can be ranked. Examples include a 5-day return, three-year debt growth, or a normalized MACD. Browse the factor library by category, such as trend and momentum, mean reversion, volatility and fund flow, or fundamentals, and add the ones you want to rank by.

Every factor in the library has already passed a quality screen, including its IC (information coefficient), turnover, fee resilience, and stability across market regimes. The IC shown on each factor measures how well its ranking has lined up with the returns that followed.

You can also skip the library and describe the idea in plain language. Minara picks the factors and writes the code for you:

> Hold the 10 cheapest, highest-quality names in TradFi 30 and short the 10 most expensive, rebalanced weekly.

> Rank Coin 30 by 30-day momentum, long the top 5 and short the bottom 5.

## Set how it trades

Set how many names to hold long, how many to short, and how often to rebalance. More names spread the risk; a shorter rebalance reacts faster but trades more, which costs more in live trading.

## Backtest, then go live

Set the date range and click Run Backtest. On each rebalance date, Minara scores and ranks the whole universe, holds the top and shorts the bottom, and reports how the portfolio would have performed. Read the metrics, then paper trade it, and deploy when the results hold up.

{% hint style="warning" %}
A strong backtest is not a promise. Factor rankings decay, and a mix tuned on one period can fail on the next. Validate in paper trading before deploying real capital.
{% endhint %}

The rest of this track explains each step in more detail: running a backtest, reading the metrics, and optimizing the factor mix.
