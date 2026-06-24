# Glossary

Plain-language definitions of the trading, market, and wallet terms used across Minara. Written for anyone new to trading.

{% hint style="info" %}
New here? Skim **Trading basics** and **Margin, leverage & liquidation** first. Those two cover most of what you need before your first trade.
{% endhint %}

## Trading basics

| Term | Meaning |
|---|---|
| Position | Your active trade on an asset. Opening a position starts the trade; closing it ends the trade and settles your gain or loss. |
| Long | A bet that a price will go up. You profit if the asset rises after you enter. |
| Short | A bet that a price will go down. You profit if the asset falls. On Minara you can short an asset without owning it first. |
| Entry / exit | The price at which you open a position (entry) and the price at which you close it (exit). |
| Spot | Buying the actual asset and owning it outright. The opposite of a derivative like a perpetual. |
| Volatility | How much and how fast a price moves. High volatility means larger, quicker swings in both directions. |
| P&L (profit and loss) | How much you have gained or lost on a trade. |
| Unrealized P&L | The gain or loss on a position you still hold. It moves with the price and is not locked in yet. |
| Realized P&L | The gain or loss that is locked in once you close a position. |
| Equity | The total current value of your account: your cash plus the unrealized P&L of any open positions. |
| Drawdown | A drop from a recent peak in your account value. |
| Max drawdown | The largest peak-to-trough drop over a period. A measure of worst-case loss. |

## Perpetuals & contracts

| Term | Meaning |
|---|---|
| Derivative | A contract whose price tracks another asset, instead of the asset itself. |
| Futures | A contract to trade an asset at a set price. Traditional futures expire on a fixed date. |
| Perpetual (perp) | A futures contract with no expiry date. You can hold it as long as you want. Minara trades crypto, stocks, and commodities as perpetuals. |
| Funding rate | A small recurring payment between long and short holders that keeps a perpetual's price near the real asset price. When positive, longs pay shorts; when negative, shorts pay longs. |
| Open interest | The total number of open positions in a market. Rising open interest means more money is flowing in. |
| Tokenized stock | A perpetual that tracks a stock's price, such as AAPL or TSLA. You trade the price movement but do not own real shares, dividends, or voting rights. |
| Altcoin | Any cryptocurrency other than Bitcoin. |

## Margin, leverage & liquidation

| Term | Meaning |
|---|---|
| Margin | The money you put up as collateral to open a leveraged position. |
| Collateral | Funds set aside to back a position. On Minara this is USDC. |
| Leverage | Trading with more size than your own funds, shown as a multiple like 10x. It multiplies both gains and losses: at 10x, a 1% price move becomes a 10% move on your margin. |
| Initial margin | The amount needed to open a position. Higher leverage means less initial margin for the same position size. |
| Maintenance margin | The minimum equity needed to keep a position open. Fall below it and the position is liquidated. |
| Margin ratio | How close a position is to liquidation. As the market moves against you, this ratio worsens. |
| Cross margin | All your funds back all your positions together. Minara's default. Spare balance can absorb a loss before liquidation, but a loss on one trade reduces the margin available to the others. |
| Isolated margin | Margin is locked to one position. A loss can only liquidate that position, without touching the rest of your balance. |
| Liquidation | When your equity falls below the maintenance margin, the system force-closes your position to stop your balance going negative. You cannot undo it. |
| Liquidation price | The asset price at which your position gets liquidated. Higher leverage moves this price closer to your entry. |
| Auto-deleveraging (ADL) | A rare last-resort backstop. In extreme moves with too little liquidity, the exchange closes some profitable traders' positions to cover liquidations. |

## Orders

| Term | Meaning |
|---|---|
| Order book | The live list of buy and sell orders for an asset. Its depth shows how much can be traded at each price. |
| Market order | Buys or sells right now at the best available price. Fast, but the exact price depends on what is available. |
| Limit order | An order to trade only at a price you set or better. It may not fill if the market never reaches your price. |
| Trigger order | An order that waits until the price hits a level you choose, then fires. |
| Stop trigger | A trigger that fires a market order when price crosses a threshold. Used for stop-losses. There is no guaranteed fill price. |
| Limit trigger | A trigger that places a limit order once the level is reached. |
| Take-profit (TP) | An order that closes your position automatically once it reaches a profit target. |
| Stop-loss (SL) | An order that closes your position automatically once a loss reaches a level you set, to cap the damage. |
| Trailing stop | A stop-loss that moves with the price as a trade works in your favor, locking in more of the gain. |
| Reduce only | A setting so an order can only shrink an existing position, never grow it or flip its direction. |
| Post only | A setting that keeps your order a maker order. If it would fill immediately as a taker, it is cancelled instead. |

## Fees & execution

| Term | Meaning |
|---|---|
| Maker | An order that adds to the order book and waits, usually a limit order. Maker fees are lower. |
| Taker | An order that fills immediately against existing orders, such as a market order. Taker fees are higher. |
| Slippage | The gap between the price you expected and the price you actually got. Larger in fast-moving or thin markets. |
| Notional / position size | The full value of your position, including the part funded by leverage. $1,000 of margin at 10x controls a $10,000 notional position. |
| Spread | The gap between the highest price buyers offer and the lowest price sellers ask. |
| Counterparty | The party on the other side of your trade. Minara is never your counterparty: trades fill against real market participants on-chain. |

## Prediction markets

| Term | Meaning |
|---|---|
| Prediction market | A market where you bet Yes or No on whether an event will happen, such as "Will BTC be above $80,000 at 2pm?" |
| Binary outcome contract | A contract with only two results. The winning side pays $1.00 per share; the losing side pays $0. |
| Implied probability | The chance the market is pricing in for an outcome. A Yes share priced at $0.65 means the market sees a 65% chance. |
| Settlement | When a contract ends and pays out based on the actual result. |
| Edge | The gap between Minara AI's estimated probability and the market's price. Positive edge means the AI sees value the market has not priced in. |
| Expected value (EV) | The average result of a bet if you repeated it many times. A positive-EV trade is statistically worth taking, though any single trade can still lose. |

## Strategy & metrics

| Term | Meaning |
|---|---|
| Backtest | Running a strategy against past market data to see how it would have performed. Strong past results do not guarantee future ones. |
| Paper trading | Testing a strategy live with fake money, so no real capital is at risk. |
| Total return | The overall percentage gain or loss over a period. |
| Win rate | The share of trades that closed in profit. |
| Profit factor | Total profit divided by total loss. Above 1.0 means the strategy made money overall. |
| Sharpe ratio | Return measured against risk. Higher is better; above 1.0 is generally considered acceptable. |
| Sortino ratio | Like the Sharpe ratio, but it only counts downside swings as risk. |
| APY (annual percentage yield) | A return rate expressed as if it ran for a full year. |
| Overfitting | When a strategy is tuned so tightly to past data that it fails on new data. |
| Cold-start bias | Lower accuracy when a strategy or model is new and has not gathered enough live data yet. |
| Trend-following | A strategy that enters in the direction of an existing trend and rides it. |
| Mean reversion | A strategy that bets a price stretched far from its average will snap back. |
| Range-bound market | A market moving sideways between a floor and a ceiling rather than trending. Also called a sideways market. |
| Grid trading | A strategy that places staggered buy and sell orders across a price range to profit from back-and-forth movement. Minara's Futures Grid works this way. |
| Market regime | The prevailing market mood, such as trending vs. ranging or risk-on vs. risk-off. |
| Whipsaw | A sharp reversal that triggers a losing trade right before the price turns back your way. |
| Reward-to-risk ratio | How much you stand to gain versus how much you risk on a trade. |

## Trading styles

| Term | Meaning |
|---|---|
| Scalping | Very short trades, in and out within minutes. |
| Day trading | Opening and closing positions within the same day. |
| Swing trading | Holding positions for days to weeks to catch larger moves. |

## Chart & indicators

| Term | Meaning |
|---|---|
| Candlestick (K-line) | A chart bar showing the open, high, low, and close price for one time period. |
| Timeframe | The time each candle covers, such as 15-minute or 4-hour. Shorter timeframes show faster detail; longer ones show the bigger picture. |
| EMA (exponential moving average) | An average price that weights recent prices more heavily, used to read trend direction. |
| RSI (relative strength index) | A 0–100 gauge of whether an asset looks overbought (high) or oversold (low). |
| MACD | An indicator that compares two moving averages to flag shifts in momentum. |
| Bollinger Bands | Bands above and below an average price that widen with volatility, used to judge whether price is stretched. |
| ATR (average true range) | A measure of how much an asset typically moves, often used to size stops. |
| Support / resistance | Price levels where an asset has tended to stop falling (support) or stop rising (resistance). |

## Wallets, funds & on-chain

| Term | Meaning |
|---|---|
| USDC | A stablecoin pegged to the US dollar. Minara's perps wallets are funded with USDC. |
| USDH | A stablecoin used to settle Hyperliquid prediction markets and some transfers. |
| Stablecoin | A crypto token designed to hold a steady value, usually $1. |
| Arbitrum | The blockchain network Minara uses to move USDC in and out. Deposits must arrive via Arbitrum. |
| On-chain | Recorded directly on a public blockchain, visible and verifiable by anyone. |
| Layer 1 / Layer 2 | A Layer 1 is a base blockchain, like Hyperliquid's own chain. A Layer 2 is built on top of another chain to make it faster or cheaper, like Lighter. |
| Custodial wallet | A wallet whose keys are managed for you. Minara uses a custodial smart wallet so you do not have to handle private keys or gas yourself. |
| Self-custody | Holding your own keys and controlling funds directly, the opposite of custodial. |
| Smart contract wallet | A wallet that is itself an on-chain program, which makes its activity auditable, rather than an entry in a company database. |
| Gas | The network fee paid to process an on-chain transaction. Minara's wallet covers this for you. |
| DEX / CEX | A decentralized exchange (DEX) runs on-chain with no central operator. A centralized exchange (CEX) is run by a company that holds your funds. |
| Perps wallet | Your trading wallet for perpetuals. Each one is tied to a single exchange, Lighter or Hyperliquid. |
| Private key | The secret that controls a wallet's funds. Anyone who has it can move the money, so never share it. |
