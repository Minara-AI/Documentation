# Deploying and live trading

**Do I need to connect my own exchange?** No. Minara runs the full deployment for you. Backtesting and paper trading happen on Minara, and when you deploy, Minara executes the trades through its own venues on Lighter and Hyperliquid. You do not connect or fund an outside exchange account.

**Can I edit a strategy after I deploy it?** Yes, but the edit does not take effect until you deploy again. A deployed strategy runs the code it had when you deployed, and changes to the draft stay in the draft. Deploy a second time to push an update.

**What happens if I stop a deployed strategy?** Stopping it closes every position it holds. There is no way to pause a deployed strategy while keeping its positions open, so stop it only when you want to exit the market.

**Why did my deployed strategy's APY reset?** APY is based on realized profit since deployment. If you stop a strategy and redeploy it, the counter starts over from the new deployment.
