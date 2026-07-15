# Data security

Minara processes trading strategies, code, wallet activity, and account data. This page explains how that data is handled, what stays private to you, what Minara can and cannot access, and the limits of that protection so you can judge it accurately.

Most analysis that turns your inputs into results runs inside a Trusted Execution Environment (TEE): a hardware-isolated region that separates a workload and its memory from the host operating system and from the people who operate the infrastructure.

## What a Trusted Execution Environment is

A TEE is an isolated processing environment enforced by the hardware. Data reaches it encrypted and is decrypted inside the sealed region before it is processed. The protection comes from isolation, not from computing on data that stays encrypted. While the workload runs, the host operating system, the hypervisor, and infrastructure operators are designed not to be able to read the workload's memory. Inputs go in, results come out, and the intermediate state is held inside the enclave rather than on the surrounding system.

A TEE protects against the operators and software layers around the workload. It does not by itself protect against flaws in the code running inside the enclave. See [What a TEE does not cover](#what-a-tee-does-not-cover) below.

## How your data is processed

Analysis runs in Minara's cloud TEE cluster. The intended data flow is:

1. Your client encrypts strategy content with a key for the enclave, so it can be decrypted only inside the TEE.
2. The ciphertext travels to Minara over TLS.
3. Minara's gateway routes the ciphertext to the cluster.
4. The enclave decrypts and processes it, then returns the result to your client.

Under normal operation, strategy content is encrypted by the client and is not available to Minara's application servers.

Encryption protects the content, not the metadata around it. Minara can still see operational metadata such as your IP address, request timing and size, your account ID, and which feature you used.

## What Minara cannot see

Under normal operation, the strategy inputs you provide are encrypted before they leave your client and are not available to Minara's application servers. The table below lists what happens to each type of input.

| Input | Minara's access |
| --- | --- |
| Strategy ideas you type | Not readable by Minara's application servers under normal operation |
| Strategy code you write or generate | Not readable by Minara's application servers under normal operation |
| Intermediate analysis inside the TEE | Isolated from the host operating system and infrastructure operators, subject to the security of the enclave workload and its permitted outputs |
| The encrypted payload in transit | Routed by Minara, decryptable only inside the enclave |

{% hint style="info" %}
This is a property of the encryption path and the enclave isolation, not only a policy commitment. It is not an absolute guarantee. What the enclave workload can access is governed by the code running inside it and the outputs it is allowed to return, and the protection holds only while the mechanisms described here work as designed.
{% endhint %}

## Encryption

Minara encrypts data at every stage where your inputs move or are held:

| Stage | Protection |
| --- | --- |
| In transit | TLS on all traffic between your client and Minara |
| Into the enclave | Strategy content is encrypted on the client with a key for the enclave, so only the enclave can decrypt it |
| In use | Data is decrypted and processed inside the sealed enclave, not on the surrounding system |
| At rest | Stored account data is encrypted on Minara's infrastructure |

TLS and the client-to-enclave encryption are two separate layers. TLS protects the connection to Minara; the client-to-enclave encryption is what keeps the content out of reach of Minara's own servers.

## How strategies are stored

When you save a strategy, it is encrypted before it is written to disk. Each strategy is encrypted with its own data encryption key, and that key is wrapped using key material derived from or authorized by your wallet. Your wallet private key itself is never transmitted to Minara.

The encrypted records are held in a database protected by several layers of access control. Even in an unexpected data breach, an attacker would obtain only the encrypted records, which stay unreadable without the wallet-derived key material needed to unwrap them.

## Data Minara does collect

Some data is needed to run your account and is handled outside the TEE analysis path. This includes:

- Account details you provide when you register, such as your email address.
- Wallet addresses and on-chain transactions, which are public by nature of the blockchain.
- Usage data such as which features you open and basic device information, used to operate and improve the product.

This data is not your strategy content. Strategy ideas and code follow the TEE path described above and are never part of this collection.

## Data retention

Account and usage data is kept for as long as your account is active, and for a limited period afterward where retention is required for legal, accounting, or security reasons. Strategy inputs processed inside a TEE are not retained by Minara in readable form, because Minara's servers and operators never have access to them in the first place.

## Third-party services

Minara relies on a small set of infrastructure and analytics providers to operate the product, for example cloud hosting and product analytics. These providers receive only the operational data needed for their function and are bound by their own data protection terms. Some analysis features may rely on an external data or model provider to work. Where they do, the data sent is limited to what the feature requires. Minara does not share your strategy content with analytics or advertising providers.

## What a TEE does not cover

A TEE protects a workload from the systems and operators around it. It is not a guarantee against every risk. It does not protect:

- Data that is already public, such as your wallet address and on-chain transactions.
- Your device if it is compromised by malware, or a strategy you choose to share yourself.
- Inputs that a result can reveal on its own.
- Bugs in the application logic, or a compromised dependency running inside the enclave.
- What happens to a strategy once it is authorized to execute.
- Correctness of a model's output.
- Custody of your funds, which is a separate matter covered by wallet security.

Side-channel and firmware-level attacks against TEEs are an active area of research, and no hardware protection is absolute.

## Your controls

- You can export your wallet private key at any time from settings, so you retain full custody of your funds.
- You can request access to, or deletion of, your account data by contacting the security team.
- You can review the permissions the app requests on your device and revoke them through your operating system.

## Reporting a security issue

If you believe you have found a vulnerability or have a question about how your data is handled, contact the Minara security team at `security@minara.ai`. Please include enough detail to reproduce the issue. Minara does not take legal action against good-faith security research.

## Changes to this statement

Minara may update this statement as the product and its infrastructure change. Material changes will be noted here, and the date below reflects the most recent revision.

_Last updated: 15 July 2026_
