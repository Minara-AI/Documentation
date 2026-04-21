# Minara Skills

## What is Minara Skills?

Minara Skills is the official skill pack that turns any compatible AI agent into a personal AI CFO. Once installed, your agent can analyze and trade crypto, US stocks, commodities, and forex; execute on-chain transactions across EVM, Solana, and Hyperliquid; manage wallets and credit-card on-ramp; and pull real-time market intelligence — all by talking to it in natural language.

Minara Skills runs on top of the [Minara CLI](https://www.npmjs.com/package/minara) and ships as a drop-in package for [Claude Code](https://claude.com/claude-code), [OpenClaw](https://docs.openclaw.ai/tools/skills), and [Hermes](https://hermes-agent.nousresearch.com/).

**What you can do with Minara Skills:**

* Buy, sell, swap, convert, and transfer spot assets by ticker, token name, or contract address across 19 networks
* Open and close perpetual futures positions on Hyperliquid with leverage, multi-wallet management, and AI autopilot
* Place, list, and cancel spot and perps limit orders
* Deposit, withdraw, and transfer between spot and perps wallets, including credit-card on-ramp through MoonPay
* Pull on-chain data, token fundamentals, whale flows, trending tokens and stocks, equity research, commodities, and forex
* Pay [x402](https://www.x402.org/)-enabled HTTP APIs directly from the Minara wallet
* Manage your Minara subscription, credits, and premium plan

***

## Who is Minara Skills For?

| User Type | Experience Level | How to Use |
|-----------|-----------------|------------|
| **Retail traders** | Any | Talk to your agent in plain English: *"Buy 100 USDC of ETH"*, *"Long ETH perp 5x"*, *"What's trending today?"* |
| **Power users & quants** | Comfortable with CLIs | Drive the underlying [Minara CLI](https://www.npmjs.com/package/minara) directly for scripting, batch jobs, and reproducible workflows |
| **Agent developers** | Building on Claude Code, OpenClaw, or Hermes | Drop the skill pack into your agent's skills directory and call Minara as a first-class tool — no glue code |

***

## How to Access

Minara Skills is distributed through GitHub: [github.com/Minara-AI/skills](https://github.com/Minara-AI/skills).

Install it into one of three supported agent runtimes (Claude Code, OpenClaw, or Hermes) using the one-click installer for that runtime, then run `Login to Minara` from inside the agent to authenticate.

You will need:

* A working install of Claude Code, OpenClaw, or Hermes
* Node.js (for `npm install -g minara`)
* A Minara account ([minara.ai](https://minara.ai))

***

## Installation

Pick the installer that matches your agent. Each one-click script installs the Minara CLI from npm, copies the skill files into the agent's skills directory, and starts the login flow.

### Claude Code

Send this prompt to your Claude Code agent:

```
Run "curl -fsSL https://raw.githubusercontent.com/Minara-AI/skills/main/scripts/claudecode-minara-skill-setup.sh | bash" to install Minara CLI, Minara Skills and set following config. Follow the login URL when prompted.
```

This installs the Minara CLI globally, copies the skill into `~/.claude/skills/minara`, and opens the login URL in your browser.

**Manual install:**

```bash
npm install -g minara@latest
git clone https://github.com/Minara-AI/skills.git /tmp/minara-skills
cp -r /tmp/minara-skills/skills/minara ~/.claude/skills/minara
```

### OpenClaw

Send this prompt to your OpenClaw agent:

```
Run "curl -fsSL https://raw.githubusercontent.com/Minara-AI/skills/main/scripts/openclaw-minara-skill-setup.sh | bash" to install Minara CLI, Minara Skills and set following config. Follow the login URL when prompted.
```

This installs the CLI, copies the skill into `~/.openclaw/skills/minara`, registers the skill in `openclaw.json`, and starts login.

**ClawHub:**

```bash
clawhub install lowesyang/minara
```

**Manual install:** clone the repo, copy `skills/minara` into your OpenClaw workspace, then add the skill to `~/.openclaw/openclaw.json`:

```json
{
  "skills": {
    "entries": {
      "minara": {
        "enabled": true
      }
    }
  }
}
```

### Hermes

Send this prompt to your Hermes agent:

```
Run "curl -fsSL https://raw.githubusercontent.com/Minara-AI/skills/main/scripts/hermes-minara-skill-setup.sh | bash" to install Minara CLI, Minara Skills and set following config. Follow the login URL when prompted.
```

This installs the Minara CLI, copies the skill into `~/.hermes/skills/minara`, and starts the login flow.

All setup scripts are idempotent. They support a three-tier skill download fallback: ClawHub → GitHub → clawhub CLI.

***

## First-Run Workflow

The fastest way to validate that the install worked end-to-end. Three commands take you from a fresh install to your first trade.

{% stepper %}
{% step %}
### Log in

Tell the agent: *"Login to Minara"*. The agent runs the CLI login command and opens a browser tab. Authenticate with your Minara account; the CLI stores the session locally.
{% endstep %}

{% step %}
### Fund your wallet

Tell the agent: *"Show my Minara deposit address"* to deposit existing crypto, or *"Buy crypto with credit card"* to on-ramp via MoonPay. To trade perps, follow up with *"Deposit 500 USDC to perps"* to move funds from spot to the Hyperliquid perps wallet.
{% endstep %}

{% step %}
### Trade

Tell the agent what you want: *"Buy 100 USDC worth of ETH"*, *"Swap 0.1 ETH to USDC"*, or *"Long ETH perp, 5x leverage"*. The agent confirms the trade details before executing. Review the **risk disclosure** carefully before approving.
{% endstep %}
{% endstepper %}

***

## Spot Trading

Spot trading covers buying, selling, swapping, converting, and transferring tokens across all [supported networks](#supported-networks). You can reference assets by ticker (`ETH`, `SOL`), name (`ethereum`), or contract address.

**Examples:**

* *"Buy 100 USDC worth of ETH"*
* *"Sell all my SOL"*
* *"Swap 0.1 ETH to USDC on Base"*
* *"Transfer 50 USDC to 0xabc..."*

The agent picks the right network and routing based on your wallet balances and the asset.

***

## Perpetual Futures

Perpetual futures are routed through Hyperliquid. You can open and close positions, set leverage, manage multiple wallets, and view trade history.

**Examples:**

* *"Long ETH perp"*
* *"Short BTC, 10x leverage"*
* *"Close my ETH position"*
* *"Show my perps history"*

### AI Autopilot

Autopilot lets the agent manage perps positions for you according to a strategy. Enable it with *"Enable AI autopilot for perps"*. Autopilot only acts within the scope you authorize, and you can disable it at any time.

> **Risk:** Perpetual futures are leveraged products. Losses can exceed your initial margin. Review the risk disclosure before enabling autopilot or opening leveraged positions.

***

## Limit Orders

Limit orders work on both spot and perps. Place an order, list open orders, and cancel by ID.

**Examples:**

* *"Buy ETH when price hits $3000"*
* *"Buy SOL at $150"*
* *"List my limit orders"*
* *"Cancel limit order [id]"*

***

## Wallet & Funds

| Action | Example prompts |
|--------|-----------------|
| **Check balance** | *"What's my balance?"* / *"Show my crypto portfolio"* |
| **Deposit** | *"Show my deposit address"* / *"Buy crypto with credit card"* |
| **Spot ↔ Perps transfer** | *"Deposit 500 USDC to perps"* / *"Withdraw 200 USDC from perps"* |
| **Withdraw on-chain** | *"Withdraw 10 SOL to [address]"* |
| **Pay** | *"Pay 100 USDC to [address]"* |

Credit-card on-ramp uses MoonPay. Withdrawals to external addresses go on-chain and incur the standard network fee.

***

## Market Intelligence

Minara Skills exposes Minara's full market intelligence stack to your agent: real-time on-chain data, token fundamentals, whale flows, trending tokens and stocks, equity research, commodities, and forex.

**Examples:**

* *"What tokens are trending?"*
* *"Search for SOL tokens"*
* *"Show me whale flows on ETH"*
* *"What's the outlook on NVDA?"*
* *"Price of gold right now"*

***

## x402 Payments

Minara Skills can pay [x402](https://www.x402.org/)-enabled HTTP APIs directly from your Minara wallet. This lets your agent call paid APIs without you handling API keys or top-ups separately.

The CLI handles the x402 handshake; you only see the agent ask for confirmation when a paid call is about to settle.

***

## Premium

Manage your Minara subscription, credits balance, and plan from inside the agent.

**Examples:**

* *"Show my credits"*
* *"Upgrade my Minara plan"*
* *"What plan am I on?"*

***

## Supported Networks

Spot trading and on-chain operations are available on:

Ethereum, Base, Arbitrum, Optimism, Polygon, Avalanche, Solana, BSC, Berachain, Blast, Manta, Mode, Sonic, Conflux, Merlin, Monad, Polymarket, XLayer.

Perpetual futures are routed through Hyperliquid.

***

## Benchmark

Minara Skills scored **88/100** on [crypto-skill-bench](https://github.com/Minara-AI/crypto-skill-benchmark) v3.0.2, evaluated on Claude Sonnet 4.6 across 76 scenarios.

| Dimension | Score |
|-----------|-------|
| Safety | 91 |
| Coverage | 86 |
| Robustness | 88 |
| Routing | 88 |
| UX | 86 |

66 scenarios passed, 10 partial, 0 failed. Safety gate: PASS.

The benchmark is open source. You can reproduce the run, inspect every scenario, and compare against other skill packs.

***

## What Minara Skills Can and Cannot Do

### What You Can Define

* The agent runtime (Claude Code, OpenClaw, or Hermes)
* The networks and assets you want to trade
* Whether to enable AI autopilot for perps, and within what scope
* Limit-order prices, leverage levels, and margin allocations
* Whether to fund via on-chain deposit or credit-card on-ramp

### What the Platform Controls

* Order routing and venue selection
* Network fees and on-chain confirmation times
* Hyperliquid liquidity, funding rates, and liquidation logic for perps
* MoonPay's KYC and pricing for credit-card on-ramp
* Skill version updates (managed by `version-check.sh` per session)

### Current Limitations

* The skill is bound to the three supported runtimes; other agent frameworks are not yet integrated.
* Direct deposits into the perps wallet are not supported. Funds must arrive via spot first, then transfer.
* Hyperliquid charges a 1 USDT fee on perps withdrawals; the skill does not waive this.
* Perpetual futures are only available on Hyperliquid. Other perps venues are not currently routed.
* Some advanced order types (TWAP, iceberg) are not exposed through natural-language prompts.

***

## Tips for Better Results

1. **Be specific about amounts and assets.** *"Buy 100 USDC of ETH"* is unambiguous; *"buy some ETH"* will trigger a clarification round.
2. **Name the network when in doubt.** *"Swap 0.1 ETH to USDC on Base"* avoids the agent having to infer routing.
3. **Confirm before approving.** The agent always shows the trade details before executing. Read them; reject if anything looks wrong.
4. **Start small.** Validate the install with a $5 swap before moving real size.
5. **Use limit orders for entries you care about.** Market orders are faster but less precise on thin pairs.
6. **Keep the CLI updated.** Run `minara --version` and compare to npm; the session-level `version-check.sh` script flags upgrades automatically.
7. **Authorize autopilot in a scope you understand.** Start with a single asset and a small margin allocation before scaling.

***

## Disclaimers

* All trading involves risk. Only trade with funds you can afford to lose.
* Perpetual futures are leveraged products. Losses can exceed your initial margin.
* Minara Skills is a tool that lets your agent operate the Minara platform. It is not financial advice.
* Minara does **not** provide liquidity or act as a counterparty. Spot routes go through external venues; perps execute on Hyperliquid.
* You retain full control. You can disable autopilot, cancel limit orders, or withdraw funds at any time.
* Historical benchmark performance does not guarantee future results.

***

## Links

* Repository: [github.com/Minara-AI/skills](https://github.com/Minara-AI/skills)
* CLI on npm: [npmjs.com/package/minara](https://www.npmjs.com/package/minara)
* Benchmark: [github.com/Minara-AI/crypto-skill-benchmark](https://github.com/Minara-AI/crypto-skill-benchmark)
* OpenClaw skills docs: [docs.openclaw.ai/tools/skills](https://docs.openclaw.ai/tools/skills)
* ClawHub: [clawhub.ai](https://clawhub.ai)
* License: MIT

<!-- Commit this file to Minara-AI/Documentation under features/minara-skills.md and add an entry to SUMMARY.md under the Features section. -->

<!-- source: https://github.com/Minara-AI/skills · generated: 2026-04-21 -->
