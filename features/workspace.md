---
description: >-
  Each Minara task has its own workspace for files, code, and results. On the
  web, it runs in a private cloud sandbox of your own. Chats can sync between
  web and desktop.
---

# Workspace

Each task in Minara has its own workspace: a place where Minara can read your files, create new ones, run analysis, and save the results for you to review. Workspaces work the same way in the web app and the desktop app.

## Web and desktop

The Minara web app and desktop app share the same interface and the same agent. Features such as suggested next steps and file previews, which used to be desktop-only, now work on the web too.

* **On the web,** every user gets a private cloud sandbox: a cloud environment of your own where your workspace files and task data are stored. It is separate from other users' sandboxes, which keeps your data more private and secure.
* **On desktop,** your workspace runs on your own computer.

A few features need your own computer, so they are only available in the desktop app, such as [computer control](#computer-control) and [Automation](../automation/overview.md). If you open one of them in the web app, Minara shows a link to download the desktop app.

## Sync across devices

You can keep your conversations in sync between the web app and the desktop app. Go to **Settings → Sync across devices** and turn on **Sync conversations**. You can also sync your personalization memories and investing profile there.

* With **Automatically** turned on, Minara keeps this device and your account in sync on its own. Turn it off to sync only when you click **Sync now**.
* If you turn syncing off, each device keeps only the conversations it recorded itself.

## What goes in the workspace

* Files you share, such as spreadsheets, documents, and screenshots.
* Scripts and code Minara writes for the task.
* Charts, reports, and other results.

Everything Minara refers to in its answer should be something you can open and check.

## Coding and analysis

Some questions need more than a quick lookup. Minara can write and run code to combine data, test an idea, or automate a repeat analysis, and keep the script so you can reuse it.

When working on your code or files, Minara:

* stays within what you asked for;
* doesn't overwrite unrelated work;
* runs checks where it can, and tells you what it verified and what it didn't.

Being able to run code does not give Minara permission to trade, move funds, or publish anything. Those still need your approval.

## Computer control

In the desktop app, you can let Minara see your screen and use other apps on your computer for a specific task. This is off by default.

<figure><img src="../.gitbook/assets/harness-computer-control.png" alt="Computer control settings in the Minara desktop app"><figcaption></figcaption></figure>

### Turn it on

In the desktop app settings, check that:

* **Screen recording** permission is granted;
* **Accessibility** permission is granted;
* computer control is turned on for your next task;
* background task control is on, if you need it and it's available.

Start with simple, read-only tasks, such as "look at this chart and summarize it", before asking Minara to click or type for you.

When computer control is on, Minara can see what's on your screen for that task. Close anything private and unrelated first. Minara does not watch your screen in the background; it only uses your screen when a task needs it.

## Passwords and API keys

Minara can know that a key or login is set up, but it never sees or shows the actual value. If something is missing, Minara asks you to add it through a secure input, not in the chat.

For how your wallet and data are protected, see [Wallet security](../technology/wallet-security.md) and [TEE-based data security](../technology/data-security.md).
