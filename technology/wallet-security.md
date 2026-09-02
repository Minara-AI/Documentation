# Wallet security

Minara creates a **non-custodial wallet for each user using EIP-7702**. Users can explore supported blockchains and interact with on-chain applications without needing to manage a separate smart contract wallet or hold gas tokens such as $ETH or $SOL.

Unlike traditional centralized exchanges, user funds remain associated with the user's **own on-chain wallet address**, rather than being represented solely as an internal balance in Minara's database.&#x20;

Through EIP-7702, the user's wallet can delegate transaction execution to a smart contract implementation, allowing Minara to provide a seamless trading and DeFi experience while keeping the wallet and its assets verifiable on-chain.

Minara does not take custody of users' assets in a centralized platform wallet. Transactions and asset movements can be independently verified on-chain.&#x20;

### **EIP-7702 Wallet**

Through EIP-7702, your own wallet delegates transaction execution to an on-chain smart-contract implementation. This gives you smart-account features: transaction execution, gas abstraction, swaps, staking, and other on-chain operations; while keeping the wallet and its assets verifiable on-chain.

* **User Wallet:** your own on-chain wallet address, which holds your assets.
* **Smart Contract Implementation:** an on-chain implementation contract that provides smart-account functionality to your wallet through EIP-7702.

The same wallet architecture and security model apply across Minara. Your perpetual trading wallets use the same wallet setup and are simply designated within the product to a specific exchange, so it is clear which venue you are trading on.

#### Key management and signing

Minara generates and operates the controlling key for your wallet on your behalf, so the Services can execute the transactions you authorize. Signing keys are protected using **Amazon Web Services Key Management Service (AWS KMS)**, including envelope encryption and strict identity and access management (IAM) controls, so keys remain within a hardened, access-controlled environment.

Operating the key on your behalf does not make Minara a custodian: you retain beneficial ownership of your assets at all times, and Minara uses this access only within the scope of your authorization and the functionality of the Services (see _Authorization and control_ below).

#### Authorization and control

* Minara executes transactions **only within the scope you authorize**, including any Autopilot activity you enable.
* This access does **not** permit Minara to move your funds to external addresses outside that scope, and Minara does **not** lend, rehypothecate, or otherwise encumber your assets.
* You may revoke your authorization (including the EIP-7702 delegation) at any time.
* You retain beneficial ownership of your assets throughout.

#### Gas abstraction (pay fees in stablecoins)

You do not need to hold a chain's native gas token to transact. Network fees are taken from your balance in stablecoins instead:

* **EVM chains:** for example, when you buy ETH with USDC on Base, you can pay the network fee in USDC rather than holding Base ETH.
* **Solana:** Solana natively supports fee sponsorship: you pay the fee in USDC, and Minara pays the underlying SOL network fee on your behalf.

Either way, you transact using assets you already hold, without separately acquiring native gas tokens.

#### Self-custody and key export

Because the wallet is your own on-chain address, you can take full self-custody at any time. You may export your wallet's private key through the in-app export flow and use it to control your assets independently of Minara. Once you export a key, its security is solely your responsibility.

#### Your responsibilities

* Keep your account credentials confidential and enable available security protections (such as two-factor authentication).
* Safeguard any private key you export. Minara cannot recover a lost or exposed exported key, and cannot reverse transactions you make outside the Services.
* Notify us via our [official Discord server](https://discord.com/invite/minaraai) or email at support@minara.ai if you suspect unauthorized access to your account.

While Minara applies industry-standard safeguards, no system is perfectly secure.

## Technical References

* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/topic-technology/software-security-guidance/overview.html)
* [AWS KMS (Envelope Encryption, IAM Policy)](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html)
