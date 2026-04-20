# Strategy Studio

## What is Strategy Studio?

Strategy Studio is Minara's AI-powered quantitative strategy creation platform. It lets you create, backtest, optimize, and deploy trading strategies — all through natural language conversation.

Whether you're a beginner with no coding experience or a seasoned trader with coding expertise, Strategy Studio meets you where you are and helps you build strategies faster than ever.

**What you can do with Strategy Studio:**

* Describe a trading idea in plain language, and AI turns it into a working strategy
* Generate trading strategy with images and videos
* Transpile the code of a trading strategy and optimize it with Minara
* Backtest your strategy against historical data to see how it would have performed
* Let AI automatically optimize your strategy for better results
* Deploy your strategy to live trading with one click

***

## Who is Strategy Studio for?

| User Type      | Experience Level                                                      | How to Use Strategy Studio                                                                                 |
| -------------- | --------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Beginners**  | No trading or coding experience                                       | Use strategy templates or describe your idea in plain language. AI handles everything.                     |
| **Traders**    | Understand indicators like RSI, MACD, moving averages, but don't code | Use the form builder to select indicators and parameters, or describe your strategy logic in conversation. |
| **Developers** | Have coding experience                                                | Import your existing code directly, and edit it with AI. AI converts, optimizes, and deploys it.           |

***

## How to Access

Access it directly via link [https://minara.ai/app/trade/strategy-studio](https://minara.ai/app/trade/strategy-studio), or navigate to **Trade** from the main sidebar on the left in Minara, then click **Strategy Studio** tab on the top.

***

## Creating a Strategy

Strategy Studio offers multiple ways to create a strategy. Choose the one that fits your workflow.

### Natural Language (Recommended for Beginners)

Type your trading idea in the chat input at the top of the homepage. You can be as simple or detailed as you want.

**Examples:**

* "Create a BTC trend following strategy"
* "I want a strategy that longs ETH when it breaks above resistance, with a 3% stop loss"
* "Build a mean reversion strategy for SOL using RSI, buying when RSI drops below 30"

Minara will first ask some clarifying questions if needed, then generate a complete strategy, automatically run a backtest, and show you the results.

**You can also attach image or video files, such as:**

* Upload a screenshot of a chart with markings, and let Minara interpret your annotations
* Upload a video explaining your strategy idea

### Strategy Templates

The homepage features curated strategy templates with real backtest data. Each template shows:

* Strategy name and type
* Style tags
* Backtest results in the detail popup

**To use a template:**

1. Browse the template cards on the strategy studio page
2. Check out any template card that interests you to see its backtest results
3. Click the "Generate Strategy" button, and directed to strategy editor page
4. Enter your preferred asset, timeframe, risk preference, and other answers of related questions Minara might ask
5. AI generates a personalized version based on the template but optimized for your choices
6. Review your backtest results

### Form Builder

Click **Form** button in the chat box section to build a strategy step by step:

1. Select your trading pair (e.g., BTC/USDT)
2. Choose a timeframe (15min, 1H, 4H, etc.)
3. Pick a strategy style (Trend Following, Mean Reversion, etc.)
4. Select technical indicators (RSI, MACD, EMA, Bollinger Bands, etc.)
5. Add any additional instructions (optional)

AI assembles your selections into a complete prompt, generates a strategy accordingly and runs the backtest.

### Code Import

Click **Code** button in the chat box to paste your existing PineScript code. Minara will:

* Convert your PineScript to Minara's execution format
* Preserve your original logic and indicator choices
* Run a backtest automatically
* Suggest optimizations if the results can be improved

***

## Understanding Backtest Results

After your strategy is created, the backtest results are displayed in two tabs: **Metrics** and **Trades**.

### Metrics

**Key Metrics (always visible):**

| Metric            | What It Means                                                        |
| ----------------- | -------------------------------------------------------------------- |
| **Total Return**  | Total profit/loss percentage over the backtest period (and $ amount) |
| **Max Drawdown**  | The largest peak-to-trough decline — measures worst-case risk        |
| **Win Rate**      | Number of winning vs losing trades                                   |
| **Profit Factor** | Ratio of gross profit to gross loss — above 1.0 means profitable     |
| **Sharpe Ratio**  | Risk-adjusted return — higher is better                              |

**Equity Curve:**

Below the key metrics, the equity curve chart shows your strategy's equity over time, compared against a buy-and-hold baseline of the same asset. This helps you see whether the strategy adds value beyond simply holding.

**Performance Analysis:**

A detailed breakdown of your strategy's profit and risk profile, including:

* Total Return vs Buy & Hold return
* Outperformance (how much you beat or trailed buy & hold)
* Expected Payoff per trade
* Long vs Short performance breakdown (return % and profit factor for each side)
* Max Drawdown, Sharpe Ratio, Sortino Ratio, and Calmar Ratio

**Trades Analysis:**

An overview of your trading activity, including:

* Total number of trades with win/loss bar visualization
* Win Rate percentage
* Largest Win and Largest Loss
* Average Profit and Average Loss per trade
* Profit Factor
* Average holding period (in bars)
* Max Consecutive Wins and Max Consecutive Losses

### List of Trades

The Trades tab lists every trade executed during the backtest, showing:

| Column              | Description                                                         |
| ------------------- | ------------------------------------------------------------------- |
| **#**               | Trade number                                                        |
| **Side**            | LONG or SHORT                                                       |
| **Entry Time**      | When the position was opened                                        |
| **Exit Time**       | When the position was closed                                        |
| **Signal**          | What triggered the exit (e.g., STOP\_LOSS, REVERSAL)                |
| **Entry Price**     | Price at entry                                                      |
| **Exit Price**      | Price at exit                                                       |
| **P\&L %**          | Profit or loss for this trade                                       |
| **MAE**             | Maximum Adverse Excursion — worst drawdown during the trade         |
| **MFE**             | Maximum Favorable Excursion — best unrealized gain during the trade |
| **Cumulative P\&L** | Running total P\&L after this trade                                 |

You can select specific trades and send them to AI as context for analysis. For example, select a few trades and ask: "Why did these trades get stopped out so early?" or "These trades shouldn't have exited here — can you adjust the exit logic?"

***

## AI Auto-Optimization

Strategy Studio automatically optimizes your strategy to aim for positive backtest results.

**How it works:**

* After generating your strategy, AI runs a backtest
* Based on the backtest result, AI may perform up to **5 optimization rounds**, trying different approaches to improve the strategy, while respecting your core requirements

**If 5 rounds aren't enough:**

AI stops and provides a detailed report of what was tried and why it didn't work, along with suggested new directions. You can pick a suggestion to start a new round of optimization, or describe your own adjustments.

**Manual optimization:**

At any time, you can ask AI to optimize in the chat:

* "Reduce the drawdown"
* "Make it trade more frequently"
* "Add a volume filter"
* "Improve the risk:reward ratio"

***

## Backtest Settings

**You can customize:**

* Number of candles (more candles = longer history = more data. It may take longer to complete the backtest with more data.)
* Timeframe (15min, 1H, 4H, Daily, etc.)
* Asset (BTC, ETH, SOL, GOLD, SILVER, etc.)

Changing any of these settings will rerun the backtest with the new configuration. The latest backtest result for each asset is saved.

***

## Deploying and Live Trading

Once you're satisfied with your backtest results, you can deploy your strategy to live trading.

{% stepper %}
{% step %}
### How to Deploy

Click **"Run"** on the top bar.
{% endstep %}

{% step %}
Select your trading wallet.
{% endstep %}

{% step %}
Review risk disclosure.
{% endstep %}

{% step %}
Confirm running.
{% endstep %}

{% step %}
The strategy is automatically deployed and running.
{% endstep %}
{% endstepper %}

### Before Going Live

* Review the risk disclosure carefully. **Historical backtest performance does not guarantee future results.**
* Make sure your wallet is idle and has sufficient funds.
  * If the wallet is running another strategy or currently has positions or open orders, the previous strategy will be stopped, positions will be closed at market price and all open orders will be cancelled.
* Make sure you understand the strategy logic. You may ask Minara to explain it to you at any time.
* Backtest the strategy on the desired asset.

### Managing Live Strategies

After deployment, you can monitor your strategy in the Autopilot dashboard:

* **Account equity** tracking
* **Open positions** with real-time updates (positions)
* **Recent trades** executed by the strategy (trade history)
* **Stop** the strategy at any time
  * Choose to keep current positions or close them at market price

### Updating your Strategy Deployment

{% stepper %}
{% step %}
Edits create a new version, so that your live strategy is not affected.
{% endstep %}

{% step %}
Backtest the new version.
{% endstep %}

{% step %}
Stop the live strategy.
{% endstep %}

{% step %}
Click **"Update"** to deploy the new version. Now the new version is deployed and can be run on live.
{% endstep %}
{% endstepper %}

Your running version is always protected. Editing and experimenting do not disrupt a running strategy.

***

## Sharing Your Strategy (Coming Soon)

### Share Card

After a backtest, click **"Share"** to generate a visual share card featuring:

* Your strategy name
* Backtest performance (PNL, drawdown, win rate)
* Profit curve chart

### How to Share

* **One-click sharing:** Opens your share panel with pre-filled text and the share card image
* **Copy link:** Copies a short link to your backtest report
* **Download image:** Saves the share card as an image to your device

### What Others See

When someone clicks your share link, they see a read-only backtest report with all your performance metrics and the AI summary. They cannot see your strategy code or modify your parameters.

From the shared report, viewers can click **"Create My Strategy"** to start their own strategy creation on Minara with your invite link.

***

## Strategy Management

### My Strategies

All your deployed strategies are saved in **"My Strategies"** accessible from the strategy selection window. Each strategy shows:

* Strategy name and description
* Creation date
* Latest backtest results
* Running status

### Version History

Strategy Studio tracks every version of your strategy:

* Each time AI generates new code, a new version is created
* Previous versions are preserved and can be viewed
* Running versions are protected and cannot be accidentally overwritten
* You can always go back to an earlier version

### Deleting a Strategy

* You can delete a strategy in the sidebar of Strategy Studio.
* If the strategy is running, you must stop it first (you may choose to keep or close positions), then you'll be able to delete it.

***

## What Strategy Studio Can and Cannot Do

### What You Can Define

* **Entry signals:** When to open a position (based on technical indicators, price action, volume, etc.)
* **Exit signals:** When to close a position (take profit, stop loss, trailing stop, signal-based exit)
* **Position actions:** Open, add to position, reduce position, close position

### What the Platform Controls

* Supported trading pairs (major crypto pairs on supported exchanges)
* Leverage is limited to levels that passed backtesting without liquidation

### Current Limitations

* **Single-asset strategies:** Each strategy trades one asset at a time (multi-asset rotation is not yet supported)
* **No external data:** Strategies are based on price and volume data from specific sources. External data (e.g. news, X posts) are not yet supported.
* **Backtest accuracy:** Backtesting uses historical candle data and does not account for partial fills or exchange-specific behavior in real trading

***

## Tips for Better Strategies

1. **Be specific:** "BTC trend strategy using EMA crossover on 4H timeframe with 3% stop loss" gives better results than "make me a profitable strategy"
2. **Start with backtesting:** Always review backtest results before deploying to live trading
3. **Manage risk:** Pay attention to max drawdown, not just profit. A strategy with +50% return and -40% drawdown is riskier than one with +30% return and -10% drawdown
4. **Iterate:** Use AI optimization or manually tweak parameters. Most good strategies take rounds of refinement
5. **Match your risk tolerance:** Be honest about how much drawdown you can stomach. AI can adjust the strategy to match your risk preference
6. **Diversify timeframes:** The same strategy logic can behave very differently on 15min vs 4H. Try multiple timeframes
7. **Be aware of "overfitting":** Use longer backtest windows for more robust results to avoid overfitting (too tailored to past events)

***

## Disclaimers

* **Historical performance is not indicative of future results.** Backtest results show how a strategy would have performed in the past, not how it will perform in the future.
* **All trading involves risk.** You may lose some or all of your invested capital. Only trade with funds you can afford to lose.
* **Strategy Studio is a tool, not financial advice.** Minara does not recommend any specific strategy or guarantee any returns. You are responsible for your own trading decisions.
* **Strategy code is transparent.** You can view, understand, and modify all strategy logic. This transparency is by design — you should understand what your strategy does before deploying it.
* **You maintain full control.** You can stop any live strategy at any time, modify your strategy, or withdraw your funds.
