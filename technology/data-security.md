# Strategy data security

This page describes how Minara protects the private content of a strategy: the ideas, instructions, parameters, code, and other material you provide to create, save, or run it. It does not describe the security of your wallet, public blockchain activity, or general account data; those have separate security properties.

For TEE-backed strategy features, Minara's operating requirement is specific: the service must provide the feature without making a strategy's plaintext available to ordinary application servers, infrastructure operators, or storage systems. The controls for that requirement are client-to-TEE encryption, attestation-gated key release, and encrypted storage. This is not a claim that no system can ever fail or that every output is incapable of revealing information.

## Scope

The protections below apply to **strategy content**:

- Strategy ideas, prompts, and instructions you enter.
- Strategy code, rules, configuration, parameters, and saved versions.
- Intermediate state created while that content is processed in the protected strategy workload.

They do not make public data private. Wallet addresses, on-chain transactions, request timing, approximate payload size, account identifiers, and feature usage may remain visible to Minara's operational systems or to the relevant blockchain. Minara minimizes and protects that operational data separately; it is not treated as strategy content.

## The protection model

Minara processes strategy content in a Trusted Execution Environment (TEE). A TEE is a hardware-backed isolated execution environment. It can protect the memory of an approved workload from direct inspection by the surrounding host operating system, hypervisor, and infrastructure administrators.

This is not “computation on data that remains encrypted.” Strategy content is decrypted while it is being used, but only inside the protected workload. The relevant security boundary is the TEE and the code measured as running inside it.

Before strategy decryption material is released, the TEE path presents a signed attestation. The strategy client, or Minara's key-release service acting on its behalf, verifies the identity and measurement of the enclave workload against an approved policy. A key is released only to a workload that satisfies that policy; it is not released to an ordinary application server.

Attestation reduces the need to trust the host running the workload. It does not establish that the measured application is bug-free, and it does not make a TEE immune to every hardware or implementation vulnerability.

## How strategy content is processed

For TEE-backed strategy features, the processing flow is:

1. The client obtains and verifies the workload's attestation against Minara's approved policy.
2. The client encrypts the strategy payload for that attested workload. The payload is also protected in transit with TLS.
3. Minara's gateway routes ciphertext to the strategy workload. It does not need the plaintext to do so.
4. Inside the TEE, the approved workload obtains the necessary key material, decrypts the payload, performs the requested strategy operation, and returns the permitted result.
5. Temporary plaintext and intermediate state are kept within the TEE's protected memory for the duration of the operation and are not intentionally written to application logs, tracing systems, or ordinary storage.

The output is part of the trust boundary. A result can reveal information about its input if the feature is designed to return it. Minara limits the workload's permitted outputs to the result required for the requested feature, but creators should not treat an output as proof that no information can be inferred from it.

## What Minara's ordinary systems do and do not receive

| Item | Handling |
| --- | --- |
| Strategy ideas, prompts, and code in a TEE-backed request | Encrypted before the protected workload receives them; not readable by Minara's ordinary application servers in the documented path |
| Strategy plaintext while in use | Decrypted only inside the TEE workload's protected memory |
| Saved strategy record | Stored as ciphertext; the database stores encrypted content and encrypted key material, not the strategy plaintext |
| Request metadata | May be processed by Minara's operational systems to provide, secure, and troubleshoot the service |
| Feature result | Returned through the feature path; it may contain information the feature is designed to reveal |

{% hint style="info" %}
These statements describe the strategy-content path, not every service component. They depend on the client verifying attestation, the key-release policy, the approved workload, and the TEE platform operating as intended.
{% endhint %}

## Encryption and key handling

Minara uses separate protections for separate stages:

| Stage | Protection |
| --- | --- |
| Client to Minara | TLS protects the network connection |
| Client to the protected strategy workload | The strategy payload is encrypted for the attested TEE workload; routing systems handle ciphertext |
| In use | The payload is decrypted only inside the TEE's protected memory |
| At rest | Each saved strategy is encrypted with a distinct data-encryption key (DEK); the DEK is stored only in wrapped form |

TLS alone protects a connection to Minara. Client-to-TEE encryption is the additional control that keeps strategy plaintext out of the ordinary gateway and application-server path.

For saved strategies, Minara uses envelope encryption: a unique DEK encrypts the strategy record, and the DEK is wrapped under key material authorized through the creator's wallet flow. Minara never receives or stores your wallet private key. Access to the encrypted record and to the wrapped key material is separately controlled; possessing a database backup alone is not sufficient to read the strategy.

Key rotation, revocation, and deletion are handled by replacing or destroying the relevant wrapping material where the implementation supports it. This is not a substitute for removing all copies required to be deleted under the applicable retention process.

## Storage and retention

Minara stores only the encrypted form of a saved strategy in its persistence layer. Strategy plaintext is excluded from ordinary databases, support tools, telemetry, and application logs. Access to encrypted records is restricted to the service components that need to store, retrieve, or serve them.

A strategy may be retained while you keep it in your account and for a limited period afterward where backup, security, or legal obligations require retention. Deleting a strategy removes it from the active product path and begins deletion from applicable systems according to Minara's retention process. Backup copies may expire on a different schedule; they remain encrypted and access-controlled until removed.

## Third parties and feature boundaries

Minara does not send strategy plaintext to analytics or advertising providers.

A feature that uses an external model or data provider may have a different data path. Minara will identify that path in the feature before strategy content is sent outside the TEE-backed strategy flow, including what content is sent and why. The protections in this page should not be read as a promise that an explicitly disclosed external-provider feature has the same TEE boundary.

## Limits of this protection

A TEE materially narrows who can access strategy plaintext, but it does not eliminate risk. The protection does not cover:

- A compromised device, browser, wallet, or account.
- Strategy content you export, share, or intentionally provide to another service.
- Bugs, malicious logic, or compromised dependencies inside the approved workload.
- Outputs that reveal information about the strategy by design or inference.
- Public blockchain data or operational metadata.
- Side-channel, firmware, or hardware attacks against a TEE platform.
- Availability, correctness of a strategy result, or custody of funds.

No hardware isolation mechanism is absolute. Minara's controls are designed to reduce access to strategy plaintext and to make that access dependent on the attested workload and authorized key flow, not to promise risk-free handling.

## Your controls

- You control whether to save a strategy and can delete saved strategies through the product where that option is available.
- You can request access to or deletion of account data by contacting the security team.
- You should keep your device, wallet, recovery material, and account credentials secure; Minara cannot protect strategy content after those are compromised or shared.

## Reporting a security issue

If you believe you have found a vulnerability or have a question about strategy-data handling, contact Minara's security team at `security@minara.ai`. Please include enough detail to reproduce the issue. Minara does not take legal action against good-faith security research.

## Changes to this statement

Minara may update this statement as the product and its infrastructure change. Material changes will be noted here, and the date below reflects the most recent revision.

_Last updated: 15 July 2026_
