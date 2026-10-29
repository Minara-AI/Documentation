# How a task works

This page follows one request from start to finish, so you know what Minara is doing and where you come in.

## 1. You describe the goal

The clearer the request, the better the result. Instead of "what should I buy?", try something like:

> Compare the current BTC setup using funding, open interest, recent price action, and my portfolio exposure. Give me the bullish case, the bearish case, the levels that would prove each wrong, and what I'd need to approve before placing an order.

A good request names the asset or question, your time horizon, and the format you want back.

## 2. Minara gathers what it needs

Minara brings in only what's relevant to your request, such as:

* your request and the conversation so far;
* live market data, news, and on-chain information;
* your portfolio and strategy information;
* files you've shared and memories you've chosen to keep.

It doesn't load everything at once. Specialized tools are brought in when the task needs them, which keeps answers focused.

## 3. Minara does the work

Minara can read market pages, run analysis, check your portfolio, write and run scripts, and, if you've turned it on, use your computer for a specific task.

Throughout, Minara keeps a clear line between what it was *asked* to do and what *actually happened*. Previewing an order is not the same as placing it, and a backtest is not the same as live performance.

## 4. Minara stops when your approval is needed

Trades, transfers, publishing anything, and other actions with real consequences always wait for you. Minara can't approve these on its own. See [Safety and approvals](safety-and-approvals.md).

## 5. You get a clear handoff

A good answer tells you:

* what was checked and which sources were used;
* what is still uncertain;
* what you'd need to approve before taking action;
* where any files or follow-ups are saved.

## About market data

Minara draws on many data providers. See [Tool Stack](../technology/tools-integration.md) for the full list. A few things to keep in mind:

* **Sources can differ.** Different venues and providers may show slightly different numbers for the same asset. Minara tells you which source it used.
* **Prices mean different things.** A reference price, a mark price, and the price you can actually trade at are not the same. Research prices are not guaranteed execution prices.
* **Missing data is not "zero".** If a source is unavailable, Minara says so instead of guessing.
* **Old results don't update.** An earlier answer shows the data as it was then. Ask again for current numbers.

## When something goes wrong

If a data source is down, a connection is missing, or a step fails, Minara tells you what actually happened. If an order or transfer may have gone through despite an error, Minara checks its status first instead of trying again, so nothing is placed twice.
