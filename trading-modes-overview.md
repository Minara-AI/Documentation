# Copilot, Autopilot, and Strategy Studio

Minara offers three ways to trade. Each suits a different level of involvement.

| Mode | Who controls execution | Best for |
|---|---|---|
| Copilot | You | Learning the market, ad-hoc trades |
| Autopilot | Minara AI | Hands-off 24/7 trading |
| Strategy Studio | Your code + Minara AI | Systematic, rules-based strategies |

## Copilot

Copilot is a chat interface where you ask Minara for trade signals and decide whether to act on them. Ask "Should I long BTC?" and Minara responds with a signal card showing direction (Long/Short), entry price, take-profit, and stop-loss. You place the trade manually.

Copilot works across all supported assets — Bitcoin (BTC), Ethereum (ETH), Solana (SOL), gold (XAU), silver, crude oil, and tokenized stocks including Apple (AAPL), Tesla (TSLA), NVIDIA (NVDA), Amazon (AMZN), and Microsoft (MSFT).

Use Copilot when you want AI input but prefer to stay in control of every order.

## Autopilot

Autopilot lets Minara open and close positions on your behalf. Set your parameters — asset, leverage (up to 25x), and risk limits — then let the AI run. It uses AI Stop-loss and AI Take-profit to manage exits, and supports Futures Grid strategies.

Use Autopilot when you want consistent exposure without watching the screen.

## Strategy Studio

Strategy Studio is a code editor where you write, backtest, and deploy trading strategies using Pine Runtime — Minara's TypeScript-based strategy language. You define entry and exit logic, run backtests against historical data, review performance metrics, then deploy. A deployed strategy runs automatically, similar to Autopilot but driven entirely by your code.

Use Strategy Studio when you have a specific hypothesis you want to test and run systematically — for example, an EMA crossover on BTC/USDT or a momentum strategy on ETH.

## How they work together

The three modes are complementary. A common progression:

1. **Start with Copilot** to get a feel for how Minara reads a market — watch the signals it generates, see how it frames entries and exits.
2. **Move to Strategy Studio** once you have an idea you want to formalize. Encode your logic in Pine Runtime, backtest it, and iterate until the metrics are sound.
3. **Run it via Autopilot or a deployed strategy** once you're confident. Autopilot handles the execution; your deployed strategy handles the logic.

You can run all three simultaneously on different assets or allocations.
