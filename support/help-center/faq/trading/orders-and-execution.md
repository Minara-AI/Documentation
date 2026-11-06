# Orders and execution

**My order didn't execute.** Before execution, Minara checks account balance, gas fees, and slippage settings. If the order failed:

* Check that your wallet has sufficient balance (including gas).
* Review the slippage tolerance — low tolerance on volatile pairs can prevent fills.
* Check the Activity log (Asset → Activity) for the error details.

If the order shows as executed but you don't see it in your position, check the correct wallet and chain.

**How does Minara handle failed trades?** Minara uses a multi-layer retry mechanism. If network congestion or price volatility occurs during execution, it adjusts gas fees and retries automatically. If the trade ultimately fails, you'll see a detailed error in the Activity log.

**Can I manually stop or pause an automated strategy?** Yes. You can pause, modify parameters, or stop any strategy at any time — including active Autopilot strategies or limit orders. This is by design; Minara's philosophy is "AI automation + human control."

**Where can I view my trade history?** Go to Asset → Activity to view all transactions and account activity.

**My Autopilot stopped running unexpectedly.** Common causes: credits ran out (Minara Call nodes consume credits), wallet connector disconnected, or the strategy hit a configured stop condition. Check your credit balance and verify the wallet connector is still active.

**My manually placed order was closed unexpectedly.** Check whether you have an Autopilot strategy running. Autopilot's order management takes priority over manually placed orders — when it adjusts or closes positions to manage risk, it can affect positions you opened manually. If you need manual orders to stay open, pause or stop any running Autopilot strategies first.

**What are the trading fees on Minara?** Minara charges a fee on each executed perpetual trade. For the current fee schedule, see the [trading fees page](https://minara.ai/docs/guide/managing-funds-and-trading/trading-fees) in the Minara documentation. Spot trading fees vary by asset and chain.
