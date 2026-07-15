# Data security

Minara processes trading strategies, code, wallet activity, and account data. This page explains how that data is handled, what stays private to you, and what Minara can and cannot access.

The core principle is simple: the analysis that turns your inputs into results runs inside a Trusted Execution Environment (TEE). A TEE is a hardware-isolated region that keeps data encrypted while it is being processed. Code and data inside it cannot be read from the outside, including by Minara.

## What a Trusted Execution Environment is

A TEE is an isolated processing environment enforced by the hardware itself. Data enters encrypted, is decrypted only inside the sealed region, is processed there, and leaves as an encrypted result. Nothing outside the enclave can inspect its memory while processing runs, not the operating system, not the host machine, and not Minara's engineers. In practice it behaves as a black box: inputs go in, results come out, and the intermediate state is never exposed.

## How your data is processed

Minara uses TEEs on both mobile and web, but the location of the enclave differs.

### On mobile: on-device analysis

On the Minara mobile app, data analysis runs entirely on your device, inside a local TEE. Your inputs are not sent to a server for this analysis. Processing happens in a sealed, isolated region of your own hardware, and the results stay on the device. Because the analysis is fully local, no strategy input leaves your phone during processing.

### On web: cloud TEE cluster

On the web app, analysis runs in Minara's cloud TEE cluster. Data is encrypted before it reaches the cluster and stays encrypted throughout. When you enter a strategy idea or code, that input goes straight into the TEE cluster for processing. Minara's servers route the encrypted payload but cannot decrypt or read it. The cluster processes the input inside the enclave and returns the result directly to your client. At no point in this path can Minara obtain your strategy ideas or your code.

## What Minara cannot see

For the strategy inputs you provide, Minara operates with zero knowledge. The table below lists what happens to each type of input.

| Input | Minara's access |
| --- | --- |
| Strategy ideas you type | Cannot read them |
| Strategy code you write or generate | Cannot read it |
| Intermediate analysis inside the TEE | Not exposed to anyone, including Minara |
| The encrypted payload in transit | Routed, but not decryptable by Minara |

{% hint style="info" %}
Zero knowledge here means Minara has no technical ability to view your strategy ideas or code during analysis, not just a policy commitment not to look.
{% endhint %}

## Encryption

Minara encrypts data at every stage where your inputs move or are held:

| Stage | Protection |
| --- | --- |
| In transit | TLS on all traffic between your client and Minara |
| Into the enclave | Strategy inputs are encrypted so that only the TEE can decrypt them |
| In use | Data is processed inside the sealed enclave and is never decrypted outside it |
| At rest | Stored account data is encrypted on Minara's infrastructure |

## How strategies are stored

When you save a strategy, it is encrypted before it is written to disk. The encryption is tied to your wallet private key, so only your key can decrypt the stored strategy. No one else can read it, including Minara.

The encrypted records are held in a database protected by several layers of access control. Even in an unexpected data breach, an attacker would obtain only the encrypted records. The strategy code stays unreadable, because decrypting it requires your private key.

## Data Minara does collect

Some data is needed to run your account and is handled outside the TEE analysis path. This includes:

- Account details you provide when you register, such as your email address.
- Wallet addresses and on-chain transactions, which are public by nature of the blockchain.
- Usage data such as which features you open and basic device information, used to operate and improve the product.

This data is not your strategy content. Strategy ideas and code follow the TEE path described above and are never part of this collection.

## Data retention

Account and usage data is kept for as long as your account is active, and for a limited period afterward where retention is required for legal, accounting, or security reasons. Strategy inputs processed inside a TEE are not retained by Minara in readable form, because Minara never has access to them in the first place.

## Third-party services

Minara relies on a small set of infrastructure and analytics providers to operate the product, for example cloud hosting and product analytics. These providers process only the operational data needed for their function and are bound by their own data protection terms. Strategy inputs handled inside the TEE are not shared with any third party.

## Your controls

- You can export your wallet private key at any time from settings, so you retain full custody of your funds.
- You can request access to, or deletion of, your account data by contacting the security team.
- You can review the permissions the app requests on your device and revoke them through your operating system.

## Reporting a security issue

If you believe you have found a vulnerability or have a question about how your data is handled, contact the Minara security team at `security@minara.ai`. Please include enough detail to reproduce the issue. Minara does not take legal action against good-faith security research.

## Changes to this statement

Minara may update this statement as the product and its infrastructure change. Material changes will be noted here, and the date below reflects the most recent revision.

_Last updated: 15 July 2026_
