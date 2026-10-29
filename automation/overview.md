---
description: >-
  Let Minara run routine work for you on a schedule, when the market moves, or on demand. Available in the Minara desktop app.
---

# Overview


{% hint style="info" %}
**Desktop only.** Automation is currently available only in the Minara desktop app. The Minara web app and mobile app do not support it yet. [Download Minara Desktop](https://minara.ai/download-app).
{% endhint %}

Automation lets Minara take care of recurring work for you. It can send you a market brief every morning, alert you when a price crosses a level, watch a wallet, track the story behind your holdings, or carry out a trading plan you have defined.

You describe what you want in plain language. Minara builds the automation, shows you exactly what it will do, and then runs it for you.

## How it works

Every automation has three parts:

| Part                    | What it decides               | Examples                                                                                                                                       |
| ----------------------- | ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Trigger**             | When does automation run      | Every day at 8:00 AM, every 15 minutes, once at a set time, when a price crosses a level, when a wallet trades, or only when you click **Run** |
| **Steps**               | What does Minara do each time | Fetch market data, check a condition, write an AI summary, prepare or place a trade                                                            |
| **Delivery (optional)** | How does Minara notify you    | In-app notification, Telegram, Discord, Slack, email, and other connected channels                                                             |

Minara picks the right kind of step for each job.

Precise work, such as comparing a price with your threshold, runs as a simple calculation, so it is fast and accurate.

Work that needs judgment, such as summarizing news or explaining a trade, is handled by Minara's AI.

### Triggers you can use

* **On a schedule**: at fixed intervals (e.g. every 5 minutes, every day, every week) or on a calendar, such as weekdays at 9:00 AM in your time zone.
* **Once only**: at one specific time, for example a reminder.
* **Manual**: only when you click **Run once**.
* **When a price crosses** / **While a price holds**: real-time price alerts. See [Price alerts](price-alerts.md).
* **When a wallet shows a possible swap** / **When an address trades perpetuals**: on-chain and perpetuals activity. See [Wallet and trader monitoring](wallet-and-trader-monitoring.md).

## What you can automate

| Use case                                                                         | Typical examples                                                                                                   |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| [Scheduled briefs and reports](scheduled-briefs-and-reports.md) | Morning market brief, daily P\&L report, weekly macro summary, reminders                                           |
| [Price alerts](price-alerts.md)                                 | "Tell me when BTC breaks $120,000", "Alert me while ETH drops below $3,000"                                        |
| [Wallet and trader monitoring](wallet-and-trader-monitoring.md) | Alerts when a wallet swaps tokens, or a Hyperliquid / Lighter trader opens a position                              |
| [Research monitors](research-monitors.md)                       | Earnings and macro calendar, sector rotation, idea screener, thesis tracker, filing alerts, prediction-market odds |
| [Automated trading plans](automated-trading-plans.md)           | Recurring buy plans, laddered orders, mirroring a wallet's trades within your limits                               |

## Create an automation

1. Open the Minara desktop app and go to **Automations**.
2. In the chatbox, describe what you want, or pick a template under **Start from a template**. For example: *"Every morning, check my portfolio and message me a summary."*
3. Answer Minara's follow-up questions. If something important is unclear, such as the asset, the time, the notification channel, or the trade size, Minara asks a short question before building anything.
4. Review the result. Minara shows the automation as a flow on the canvas: the trigger, each step, and the message you will receive.
5. Minara saves the automation. If everything it needs is already connected, it turns on right away. If a messaging channel or credential is missing, it stays off and Minara tells you what to set up.

You can keep refining in the same chat, for example *"change it to every weekday"* or *"send it to Telegram instead"*. Minara updates the same automation instead of creating a new one.

## Test, run, and manage

Open the **Manage** tab to see every automation and its status (**Active**, **Paused**, or **Archived**). From an automation's page you can:

* **Test**: run the steps once with sample data to check the result. Trades, transfers, and other actions that need your confirmation are not executed during a test.
* **Run once**: run it immediately, without changing its schedule.
* **Automatic execution**: turn the trigger on or off.
* **Edit schedule**, **Adjust conditions**, or **Edit notification**: change when it runs, what it watches, or what it sends.
* **Run history**: see each run's status (Running, Succeeded, Failed, Waiting, Canceled) and what each step produced. If a run fails, click **Diagnose in chat** and Minara will help you fix it.
* **Archive**: stop the automation and cancel any runs in progress. You can restore it later; it comes back paused.

### Approvals and permissions

Some steps need your go-ahead, such as placing a trade or moving funds. When a run reaches one of these steps, it waits and shows **Waiting for your approval**. Click **Approve** to continue or **Reject** to stop the run.

Each automation's **Execution permissions** control how much it can do without asking:

| Mode               | What happens                                                               |
| ------------------ | -------------------------------------------------------------------------- |
| **Ask each time**  | You confirm every action.                                                  |
| **Approve for me** | A reviewer agent approves ordinary actions. You still confirm money moves. |
| **Auto mode**      | Actions run automatically. You still confirm money moves.                  |
| **Hands-off**      | Everything runs automatically, including trades and transfers.             |

{% hint style="warning" %}
Only use **Hands-off** for automations you have tested and fully understand. In this mode, trades and transfers run without asking you first.
{% endhint %}

## Notifications

* **In-app notification** works right away and needs no setup. Results appear in the notification center.
* **Telegram, Discord, Slack, email, WhatsApp, and Signal** must be connected in **Settings** first. Entering a recipient address in the chat is not enough. An automation that depends on a channel you have not connected stays off until you connect it.

## Credits and fees

* Steps that use Minara's AI, such as writing a summary or analyzing news, consume [credits](../reference/credits.md) each time they run.
* Simple checks, such as comparing a price with your level, do not need the AI. For alerts that run every few minutes, ask Minara to check the price directly instead of running an AI analysis each time.
* Trades placed by an automation are charged the same [trading fees](../trade/trading-fees.md) as manual trades.

## Limitations

* **Desktop only.** Automation runs in the Minara desktop app. The web app and the mobile app do not support it yet.
* <mark style="color:orange;">**Keep the desktop app running.**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">Schedules and real-time monitors run on your computer. If the app is closed, offline, or your computer is asleep, runs and alerts can be delayed or missed.</mark>
* **Connections come first.** Messaging channels, API keys, and accounts such as Gmail must be connected before an automation that uses them can turn on.
* **Keep flows focused.** Very long, multi-branch automations are harder to keep reliable. Split a complex job into a few smaller automations.
* **AI output can be wrong.** Review AI summaries and analysis before acting on them, and double-check important numbers.
* **Not a strategy engine.** To run a quantitative trading strategy continuously, use [Autopilot](../features/trading-autopilot.md) or [Strategy Studio](../trade/strategy-studio/README.md) instead.

Looking for the old web Workflow docs? See [Legacy: Web Workflow](legacy-workflow/README.md).
