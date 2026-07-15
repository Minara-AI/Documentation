# Strategy data security

This page explains how Minara handles the private parts of your strategy: your ideas, prompts, code, rules, settings, and saved versions.

Minara uses [Privy](https://www.privy.io/), a widely used provider of embedded user wallets, for wallet services. An authorized Minara service can request the wallet operation needed to run a feature. In plain terms, this is **not** end-to-end encryption from Minara: Minara may process strategy data when it needs to provide the feature you asked for.

We protect that access with sign-in checks, access controls, encrypted storage, and isolated processing for sensitive workloads.

## Overview

<figure><img src="../.gitbook/assets/strategy-data-security-overview.png" alt="Five steps for strategy data: you send a request, Minara checks access, Privy handles the wallet operation, a protected worker processes the strategy, and the encrypted strategy is stored."><figcaption><p>A simple view of how strategy data moves through Minara.</p></figcaption></figure>

## In brief

- Your request is encrypted while it travels to Minara (TLS).
- Minara checks that you are signed in and that the request is allowed.
- Privy helps protect the wallet key used for approved wallet operations. Minara's authorized services can request those operations, but ordinary servers do not receive an exportable full private key.
- An authorized worker processes the strategy. For sensitive workloads, a TEE adds an extra layer of isolation while the worker runs.
- Saved strategies are stored as encrypted records with protected key material.

## What happens when you use a strategy feature

1. You send a request to save, run, or update a strategy.
2. Minara checks your session and applies the access rules for that feature.
3. If the feature needs a wallet operation, an authorized Minara service requests it through Privy.
4. The strategy worker processes the data needed for the feature and returns the result.
5. If you save the strategy, Minara stores an encrypted version.

Minara does not use strategy plaintext in analytics or advertising tools. We also aim to keep it out of ordinary logs, support tools, and telemetry.

## Wallets and keys

Privy is the wallet service used by Minara. Its protected environment performs approved wallet-key operations. In the normal path, Minara's ordinary servers receive the result of that operation, not a complete private key that can be exported.

However, because Minara can request approved operations through this wallet path, a wallet is not a promise that Minara can never access strategy data. The wallet, access rules, and encryption work together to limit and protect that access.

## What a TEE means

A Trusted Execution Environment (TEE) is a protected area for running software. It helps keep a worker's memory separate from the surrounding server while it is running.

Your strategy is decrypted only when the authorized worker needs to use it. A TEE adds protection around that step, but it does not make Minara unable to access data through an approved service, and it cannot protect against every software or hardware vulnerability.

## What Minara may handle

| Data | How it is handled |
| --- | --- |
| Strategy data | Processed by an authorized worker when needed for a feature. |
| Saved strategy | Stored as encrypted data. |
| Wallet operation | Requested by an authorized Minara service through Privy when a feature needs it. |
| Wallet private key | Not normally available to Minara's servers as a complete, exportable key. |
| Account and request details | Used to run, secure, and support the service. |
| Feature result | Returned to you; it may reveal information that the feature is designed to show. |

## Storage and deletion

Minara keeps saved strategies in encrypted form. When you delete one, we remove it from the active product path and begin deletion from the relevant systems. Encrypted backup copies may remain for a limited time before they expire.

## Important limits

No security system removes every risk. This page does not protect against a compromised device or account, a strategy you choose to share, an output that reveals strategy details, public blockchain data, or every possible software and hardware vulnerability.

Some features may use an external model or data provider. If a feature sends strategy data outside Minara's normal protected path, it should tell you what is sent and why.

## Questions or security reports

If you have a question about strategy-data handling or believe you found a security issue, contact `security@minara.ai`.

## Changes to this statement

Minara may update this statement as the product and its infrastructure change. Material changes will be noted here, and the date below reflects the most recent revision.

_Last updated: 15 July 2026_
