# Sovereign architecture

DMind-3 is built as a three-layer system called the Edge-Local-Cloud sovereign stack. Each layer is a different model, runs in a different place, and has a different job. The design separates safety-critical work from strategy work from market-wide work, so each piece can be the right size and run in the right environment.

## The three layers

| Layer | Model | Where it runs | Job |
|---|---|---|---|
| Edge | DMind-3-Nano (270M) | Browser, wallet, mobile | Deterministic transaction safety checks |
| Local | DMind-3-Mini (4B) | User's device | Private strategy and research reasoning |
| Cloud | DMind-3 (21B) | Cloud API or private VPC | Cross-market, cross-chain analysis |

## Edge: deterministic intent firewall

When a user is about to sign a transaction, DMind-3-Nano parses the calldata locally and checks it against a fixed set of high-risk patterns: unlimited approvals, transfers to newly deployed contracts, suspicious delegate calls, interactions with known phishing addresses.

The check is rule-based rather than probabilistic. A small on-device model is well-suited to this kind of fixed-pattern recognition, and the model never sends transaction data anywhere. If the network is down or the cloud service is unavailable, Nano still works.

{% hint style="warning" %}
The reason this layer matters: a transaction signed on chain cannot be undone. There is no chargeback, no support ticket, no 24-hour cooling-off period. Safety has to happen before the signature, not after.
{% endhint %}

## Local: private reasoning engine

DMind-3-Mini runs on a user's device and handles work that touches private information: analyzing a wallet's holdings, drafting a strategy around specific positions, reading research with the user's portfolio as context.

Mini is trained to question its own answers (see [Training methods](training-methods.md) for the C³-SFT method). For each question it generates an initial answer, then enters a reflection step where it looks for errors in its own reasoning before producing a final answer. This reduces the failure mode where a small model confidently states something wrong.

## Cloud: market-wide oracle

DMind-3, the 21B cloud model, has the global view. It runs in the cloud or a private VPC and handles work that needs market-wide context:

* Cross-chain capital flow analysis across Ethereum, Solana, Cosmos, and major L2s.
* Market regime detection, predicting transitions between volatility states, funding rate environments, and liquidity conditions.
* Systemic risk modelling, simulating cascading liquidation paths across DeFi protocols.
* Long-form research reports on protocols, tokenomics, and competitive positioning.
* Agent fleet orchestration, where many local Mini and Nano instances coordinate through the Oracle.

The Oracle has a 256k-token context window. This matters because a single DeFi audit report can run to 100,000 tokens before any comparison material is added.

## How requests get routed

Requests are routed between the layers based on two questions: how privacy-sensitive is this, and how confident is the local model.

A request that touches private information (wallet balances, trading intent, identity) stays local. Even if Mini is uncertain, the data does not leave the device. A request that is not privacy-sensitive but needs market-wide context goes to Oracle, with personal details stripped before sending. A request that is not privacy-sensitive and that Mini is confident about stays local anyway, because there is no reason to round-trip to the cloud.

This inverts the usual cloud-first model. The default is local. The cloud is a restricted helper for things that genuinely need a global view.

## The Policy Gate

Any answer Oracle returns has to come back through the Edge layer before it can trigger a wallet action. The cloud is not allowed to sign anything directly. Nano runs its safety checks on whatever transaction the cloud suggested, and the user signs only after that gate passes.

Execution authority lives at the edge.
