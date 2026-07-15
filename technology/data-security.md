# Data Security

Minara handles trading strategies, code, wallet activity, and account data. Your strategy remains your own: Minara uses your prompts and code only to provide the feature you request. We do not copy strategies, publish them, sell them, or use them to train shared models. Strategy code is shared with other users only when its creator chooses to open-source it.

Minara uses [Privy](https://www.privy.io/), a widely used provider of embedded user wallets, for wallet services. An authorized Minara service can request the wallet operation needed to provide a feature. This lets the feature work without exposing a complete private key to ordinary Minara servers.

## What a Trusted Execution Environment is

A Trusted Execution Environment (TEE) is a hardware-isolated place to run software. Strategy data is decrypted only when the authorized worker needs it, and the TEE helps keep that worker's memory separate from the surrounding server while it runs.

A TEE protects a workload from the systems around it. It does not make Minara unable to access data through an approved service, and it does not protect against every software or hardware vulnerability. See [What a TEE does not cover](#what-a-tee-does-not-cover) below.

## How your data is processed

Strategy features run through Minara's protected processing path:

1. Your request travels to Minara over TLS.
2. Minara checks your session and the access rules for the feature.
3. If a wallet operation is needed, an authorized Minara service requests it through Privy.
4. An authorized worker processes the strategy. A TEE adds isolation for sensitive workloads while they run.
5. If you save the strategy, Minara stores an encrypted version.

Encryption protects the connection and stored records, but not every detail around them. Minara can still see operational data such as your account ID, request timing and size, and which feature you used.

## How Minara protects your strategy

Strategy content is used only inside the protected service path for the feature you request. It is not shared with other users and is kept out of ordinary logs, support tools, telemetry, analytics, and advertising systems.

| Input | How Minara protects it |
| --- | --- |
| Strategy prompts you write | Used only to provide the feature you request; never shared with other users |
| Strategy code you write or generate | Private by default; shared with other users only if you choose to open-source it |
| Intermediate work inside a TEE | Kept inside the protected worker while it runs, away from the surrounding host system |
| Saved strategy | Stored as encrypted data with protected key material |
| Wallet private key | Not passed to ordinary Minara servers as a complete, exportable key |

Privy protects wallet-key operations. An authorized Minara service can request an approved operation, but ordinary servers do not receive a complete private key that can be exported.

## Encryption

Your connection to Minara uses TLS, and saved strategies are encrypted with protected key material. Privy governs approved wallet operations, while a TEE adds isolation when strategy data is being processed. Together, these controls keep strategy use limited to the feature you request and prevent routine access.

## How strategies are stored

When you save a strategy, it is encrypted before it is written to disk. Each strategy uses its own data-encryption key, and the database stores the encrypted record and protected key material rather than the strategy plaintext.

Access to a saved strategy requires the relevant protected key material and an authorized service path. A database backup alone should not be enough to read a saved strategy.

## Data Minara does collect

Some data is needed to run your account and is handled outside the strategy-processing path. This includes:

- Account details you provide when you register, such as your email address.
- Wallet addresses and on-chain transactions, which are public by nature of the blockchain.
- Usage data such as which features you open and basic device information, used to operate and improve the product.

This is operational data. Strategy prompts and code are handled through the protected path described above when you use a strategy feature.

## Data retention

Account and usage data is kept for as long as your account is active, and for a limited period afterward where retention is required for legal, accounting, or security reasons. Saved strategies remain encrypted while stored. When you delete a strategy, Minara removes it from the active product path and begins deletion from the relevant systems. Encrypted backup copies may remain for a limited time before they expire.

## Third-party services

Minara relies on infrastructure and analytics providers to operate the product. These providers receive only the operational data needed for their function. Minara does not share strategy plaintext with analytics or advertising providers.

Some features may rely on an external data or model provider. Where they do, the feature should explain what data is sent and why. That feature may have a different data path from the one described on this page.

## What a TEE does not cover

A TEE is an important protection layer, but it is not a guarantee against every risk. It does not protect:

- Data that is already public, such as your wallet address and on-chain transactions.
- Your device if it is compromised, or a strategy you choose to share.
- Inputs that a result can reveal on its own.
- Bugs in the application logic, or a compromised dependency running inside the workload.
- Correctness of a model's output.
- Custody of your funds, which is a separate matter covered by wallet security.

No hardware protection is absolute. TEE isolation reduces exposure while a workload runs; it does not remove the need for secure software and access controls.

## Your controls

- You can export your wallet private key at any time from settings, so you retain full custody of your funds.
- You can request access to, or deletion of, your account data by contacting the security team.
- You can review the permissions the app requests on your device and revoke them through your operating system.

## Reporting a security issue

If you believe you have found a vulnerability or have a question about how your data is handled, contact the Minara security team at `security@minara.ai`. Please include enough detail to reproduce the issue. Minara does not take legal action against good-faith security research.

## Changes to this statement

Minara may update this statement as the product and its infrastructure change. Material changes will be noted here, and the date below reflects the most recent revision.

_Last updated: 15 July 2026_
