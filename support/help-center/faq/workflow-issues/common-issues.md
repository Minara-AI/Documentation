# Workflow troubleshooting

**My workflow was deployed but didn't do anything.** Common causes: the trigger condition wasn't met, a required connector (Telegram, email, exchange) is missing or unauthorized, or the workflow uses a node type that isn't fully supported yet.

What to check:

* Confirm the workflow is based on a supported template (price alert, automated trade, scheduled analysis, copy trading).
* Verify all connectors are correctly linked and authorized in your settings.
* Review each node's logic to confirm inputs are valid.

Open a Discord ticket with your workflow ID if the issue persists.

**My price alert triggered once and then stopped.** This is expected. Price-triggered workflows are one-shot by design — each branch executes once when the condition is met, then ends. For continuous monitoring, set multiple price-triggered branches in one workflow, or use a scheduled workflow instead.

**I set up an email alert but never received anything.** Common causes:

* The workflow failed before reaching the email node (check workflow logs).
* The email connector is not verified or authorized.
* The email went to spam.
* Credits ran out before the email node executed.

Check your spam folder and verify your email connector settings. Open a Discord ticket with your workflow ID if needed.

**My workflow stopped running after some time.** Most likely cause: credits ran out. All active workflows pause automatically when subscription credits are fully consumed. Check your credit balance and top up or upgrade your plan if needed.

**Can I set multiple price targets in one workflow?** Yes. Add multiple price-triggered branches — each fires independently when its condition is met. For continuous monitoring of the same price level, use a scheduled workflow.

**What workflow types are stable and supported?** Currently stable:

* Price alert bot
* Automated trade with TP/SL
* Scheduled analysis report
* Copy trading bot

Custom workflows outside these templates may not be fully supported yet.
