# Minara Bug Bounty Program

Minara's bug bounty program rewards responsible disclosure of vulnerabilities that threaten funds, authorization boundaries, or sensitive information. Reports are assessed by the damage an exploit can cause and how feasible it is in practice, with priority given to reproducible findings that demonstrate real security impact.

## Security impacts we cover

This program covers Minara-controlled code, services, and integrations across **Agent, Desktop, Web, Mobile, and API** products.

* **Accounts and access:** account takeover, session compromise, authentication or 2FA bypass, recovery flaws, and cross-user access.
* **Wallets and signing:** unauthorized signatures or transfers, private-key export flaws, incorrect wallet ownership checks, signature replay, and delegation or transaction authorization failures.
* **Trading and transfers:** bypassing approved wallets, assets, amounts, recipients, chains, or execution limits; unauthorized or duplicate orders; deposit, withdrawal, refund, and accounting manipulation.
* **Autopilot and strategies:** unauthorized activation or changes, trading beyond approved scope, revocation bypass, and manipulation of strategy execution or settlement.
* **Strategy Studio and Marketplace:** execution isolation failures, private strategy source-code exposure, unauthorized strategy changes, subscriber access flaws, and profit-share manipulation.
* **Workflows:** unauthorized access or execution, trigger and callback flaws, unsafe retries, code isolation failures, and credential exposure.
* **Agents and client applications:** prompt injection, tool misuse, sandbox escape, or client permission flaws that cause unauthorized actions, data disclosure, credential exposure, or privilege escalation.
* **APIs and payments:** API-key authorization flaws, payment-proof replay, unauthorized charges, and exploitable billing, credits, fee, or gas-sponsorship abuse.
* **User and internal data:** unauthorized access to or disclosure of user records, private conversations, internal documents, proprietary source code, operational logs, business or financial information, credentials, and other confidential Minara data. Severity depends on sensitivity, scope, and practical consequences.
* **Infrastructure:** unauthorized execution or access to Minara systems through a vulnerability in the covered products.

## Out of scope

* AI hallucinations, inaccurate predictions, prompt disclosure, or model-policy bypass without a demonstrated security impact.
* Normal trading losses, liquidation, slippage, funding costs, liquidity constraints, or backtest/live-performance differences.
* Scanner output, version disclosures, missing best-practice controls, or theoretical issues without a viable impact and reproduction path.
* Self-XSS or actions confined to a researcher's own environment that do not cross an intended security boundary. Deliberately enabled local capabilities are not vulnerabilities by themselves.
* Vulnerabilities solely in third-party products, protocols, or infrastructure, without a root cause in Minara-controlled code or configuration.
* Phishing, social engineering, physical attacks, credential stuffing, brute force, spam, and pure DoS/DDoS.
* Ordinary referral, promotional, or multi-account abuse without a security boundary violation or material accounting flaw.
* Issues confined to unsupported versions that do not affect a currently supported Minara product.

Availability flaws that can freeze funds, block necessary risk controls, or enable theft may qualify when demonstrated safely.

## Severity & Likelihood

Each eligible report receives two ratings: **Severity (S1–S4)** for the consequences of exploitation, and **Likelihood (L1–L3)** for practical exploitability. For example, S4 / L1 means Critical impact with difficult exploitation conditions.

### Severity

| Tier          | Impact                                                                                                                                                                        |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| S4 — Critical | Rapid, widespread theft of funds, or signing/execution compromise that directly enables equivalent damage with little effective response time.                                |
| S3 — High     | Large or rapid theft, permanent fund freezing, serious account compromise, or extensive exposure of highly sensitive user or internal data, credentials, or proprietary code. |
| S2 — Medium   | Bounded or slower financial damage, temporary fund freezing, or a limited but material authorization or confidential-data breach.                                             |
| S1 — Low      | Demonstrated minor security impact or small economic damage.                                                                                                                  |

### Likelihood

| Tier        | Conditions                                                                                                                                                   |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| L3 — High   | Reliably exploitable by an ordinary external attacker without unusual state, timing, or additional victim interaction.                                       |
| L2 — Medium | Requires realistic but specific timing, state, capital, or normal user interaction with attacker-influenced content.                                         |
| L1 — Low    | Requires independently rare conditions, a hard-to-control window, exceptionally high unrecoverable costs, or another demonstrated but difficult attack path. |

Assuming an already-compromised administrator or stolen private key does not establish an eligible vulnerability.

### Classification examples

These examples are hypothetical. Final ratings depend on the demonstrated impact and prerequisites.

| Demonstrated scenario                                                                                                | Rating  |
| -------------------------------------------------------------------------------------------------------------------- | ------- |
| An ordinary account can reliably bypass signing authorization and rapidly drain many wallets.                        | S4 / L3 |
| Equivalent fund theft requires a settlement window the attacker cannot reliably create.                              | S4 / L2 |
| Equivalent fund theft requires two independently rare recovery states, with a proven attack path.                    | S4 / L1 |
| An ordinary account can reliably access extensive highly sensitive internal records or private strategy code.        | S3 / L3 |
| Normal Agent retrieval of malicious content triggers a large unauthorized financial action.                          | S3 / L2 |
| A rare combination of recovery and authorization states permanently locks user funds.                                | S3 / L1 |
| A repeatable fee-validation flaw causes losses bounded by a non-bypassable global cap.                               | S2 / L3 |
| A refund race causes limited duplicate refunds in a window the attacker cannot reliably create.                      | S2 / L2 |
| Several rare settlement conditions cause temporary, recoverable fund freezing.                                       | S2 / L1 |
| A reliably accessible disclosure has minor security impact and no path to sensitive data, credentials, or funds.     | S1 / L3 |
| A tightly bounded billing flaw requires a specific sequence with conditions outside the attacker's reliable control. | S1 / L2 |
| A rare configuration combination causes a minor security disclosure with no escalation path.                         | S1 / L1 |

## Rewards

| Severity      | L3 — High likelihood       | L2 — Medium likelihood     | L1 — Low likelihood        |
| ------------- | -------------------------- | -------------------------- | -------------------------- |
| S4 — Critical | Negotiated; up to $300,000 | Negotiated; up to $300,000 | Negotiated; up to $300,000 |
| S3 — High     | Negotiated; up to $300,000 | $25,000                    | $10,000                    |
| S2 — Medium   | $5,000–$10,000             | $2,000–$5,000              | $500–$2,000                |
| S1 — Low      | $250–$500                  | $100–$250                  | $50–$100                   |

All amounts are in **USDC, per unique vulnerability**. Eligible S3 / L2 and S3 / L1 reports receive the fixed amounts shown. S1 and S2 awards fall within their corresponding ranges.

S3 / L3 and all S4 awards are negotiated based on demonstrated impact and exploitability, with no guaranteed fixed payout. The $300,000 maximum applies once per unique vulnerability, including its associated attack chain.

We consider the users and systems practically affected, data sensitivity, loss limits, recoverability, and effective controls. Claimed exposure of all platform funds must be demonstrated, not assumed. A valid report does not lose value because we subsequently detect or fix the issue.

## Safe testing

Use local reproductions, chain forks, or test environments wherever possible. Production testing must be low-volume, non-disruptive, and limited to accounts and assets you control. Do not conduct high-volume or indiscriminate automated scanning.

Do not access or modify another person's data, move their funds, cause liquidations, manipulate live markets, or distribute payloads through public strategies or shared content. Do not test third-party systems without their authorization.

Stop once you have sufficient evidence. If you encounter user or internal confidential data, do not explore further or retain unnecessary copies; report the exposure privately. Contact us before any further validation that could cause harm.

## Reporting a vulnerability

Email reports to [**security@minara.ai**](mailto:security@minara.ai) and copy [**team@minara.ai**](mailto:team@minara.ai).

Subject: `Bug Bounty Report — [Affected Product] — [Short Summary]`. Prefix `[URGENT]` for suspected ongoing theft or credential compromise.

Include:

1. Affected product, environment, and version.
2. Root cause, required permissions, and attack conditions.
3. Reproduction steps and expected versus actual behavior.
4. A minimal PoC and relevant redacted logs or transaction hashes.
5. Demonstrated impact, affected scope, and limitations.

S3/S4 reports require a runnable PoC or equivalent safe reproduction. For S2, a PoC is preferred; S1 requires clear reproduction steps. If reproduction would risk funds or data, submit existing evidence first and arrange validation with us.

Do not email private keys, seed phrases, or unnecessary personal data. Contact us to arrange secure delivery of sensitive evidence. Keep vulnerability details out of public chat, social media, and public issue trackers.

## Eligibility, duplicates, and review

The first sufficiently complete, reproducible report of a previously unknown, eligible vulnerability qualifies for a reward, subject to these rules.

Reports sharing a root cause are assessed together. The same attack chain does not receive multiple rewards; independent root causes may qualify separately. Duplicates do not normally receive separate awards. An internally known issue must have a timestamped record predating submission that establishes the same root cause.

Current Minara employees and contractors responsible for developing, auditing, or securing the affected systems are excluded. Contracted assessments follow their own agreements.

We explain eligibility, ratings, and award decisions. Researchers may request review and provide additional evidence.

## Response and payment

Suspected Critical and High incidents affecting funds, credentials, or highly sensitive data are escalated on triage. Remediation complexity does not indefinitely postpone an agreed award.

Rewards are paid in **USDC**. Researchers may choose **Ethereum mainnet (ETH), Solana (SOL), or BNB Smart Chain (BNB)** as the payment network.

## Coordinated disclosure and good-faith research

Please coordinate publication with us after remediation and validation, removing details that could expose users or active systems. Public credit is optional.

For good-faith research complying with this program, Minara will not initiate or support legal action based solely on that research, or treat it as a violation of applicable service restrictions. This commitment does not authorize testing third-party systems or bind third parties.

Program changes apply prospectively. Reports are evaluated under the terms in effect when submitted.
