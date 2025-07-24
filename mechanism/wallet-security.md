# Wallet Security

## Introduction

One major advantage of Minara is that she creates a **custodial** smart wallet for each user. Users can effortlessly explore any blockchains without gas tokens(like $ETH or $SOL) or learning crypto wallets.

Unlike traditional centralized exchanges, **this custodial smart wallet is not stored in Minara's internal database, but is an on-chain smart contract wallet**. Minara can manage the funds in this wallet but cannot hide, delete or blacklist it. In the future, users will have the ability to customize how Minara utilizes their funds.

To elaborate, Minara's wallet system involves two types of wallets:

* **Funding Wallet**: An automatically generated smart contract wallet for each user, storing the funds they deposit.
* **Controller Wallet**: A wallet controlled by Minara that can manage the Funding Wallet and its funds, conducting transactions, staking, and other on-chain operations. This wallet uses advanced cryptography technology such as key sharding, multi-signature, and TEE to ensure security while maximizing signature efficiency.

## Funding Wallet

Funding wallet is based on [Universal Account](https://developers.particle.network/intro/universal-accounts) by Particle Network.&#x20;

* Built on the ERC-4337 standard.
* Compatible with existing EOA wallets.
* Support social login integration.

## Controller Wallet

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

Minara's Controller Wallet leverages Privy, TEE (Trusted Execution Environment) and a multi-party authorization signing mechanism. Its core features include:

* **Sharded Key Management & TEE Custody**: Keys are encrypted and stored in shards across different security boundaries. They are encapsulated and retrieved within the TEE, ensuring they always remain in a trusted environment.
* **M-of-N Authorized Signatures**: Multi-party authorization enhances transaction security. Independent services like business, risk control, and strategy services contribute to signature verification, minimizing single points of failure.
* **Service Signature Key Protection**: AWS KMS provides independent protection for key signatures.
* **Account Policy Control**: Supports customizable permission policies based on account types and user dimensions, dictating transfer permissions, contract types, transaction limits, and more.

## Technical References

* [Privy & TEE Custody + Sharded Key Management](https://docs.privy.io/security/overview)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/topic-technology/software-security-guidance/overview.html)
* [AWS KMS (Envelope Encryption, IAM Policy)](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)
