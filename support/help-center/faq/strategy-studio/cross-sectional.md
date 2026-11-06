# Cross-sectional strategies

**What is a cross-sectional strategy, and when should I use it?** It trades a basket of assets by ranking them against each other, so it answers selection: which assets to hold. It scores every asset in a universe with one or more factors, holds the top of the ranking long and the bottom short, and rebalances on a schedule. Because the long and short legs roughly balance, much of the market's overall move cancels between them.

**What universes can I choose from?** TradFi 30 covers 30 traditional finance names, Coin 30 covers 29 crypto assets, and Coin 50 covers 49 crypto assets. The universe is the pool of assets your strategy ranks and picks from.

**What is a factor, and what does its IC mean?** A factor is a rule that turns each asset into a score, applied the same way to every asset so they can be ranked, such as a 5-day return or a normalized MACD. The IC (information coefficient) shown on each factor measures how well its ranking has lined up with the returns that followed. Every factor in the library has already passed a quality screen on IC, turnover, fee resilience, and stability across market regimes.

**How do the long and short counts and the rebalance affect it?** The counts set how many names you hold on each side, and more names spread the risk. The rebalance sets how often the strategy re-ranks and trades. A shorter rebalance reacts faster but trades more, which costs more in live trading.

**What does Optimize do for a cross-sectional strategy?** It asks Minara to tune the strategy for you. Minara tests variations of the factor weights, the factor set, the long and short counts, and the rebalance frequency, then ranks them by your target metric so you can apply a variation that beats your current mix.
