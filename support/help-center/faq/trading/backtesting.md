# Backtesting

**How does Strategy Studio simulate trailing stops and other intrabar orders?** Strategy Studio runs the strategy on OHLC candles at the timeframe you choose. For take-profit, stop-loss, trailing-stop, and limit orders, it checks lower-timeframe candles inside each strategy bar to determine when the trigger fired. This provides intrabar precision similar to TradingView's Bar Magnifier instead of relying only on the strategy candle's close.

The engine still uses candle data rather than individual ticks. It is designed for strategies that make decisions on candle timeframes, not for high-frequency or tick-level execution research.
