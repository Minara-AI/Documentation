# TEE-based Data Security

<table><thead><tr><th width="335.14373779296875">Document positioning</th><th>Version and date</th></tr></thead><tbody><tr><td>External statement for full-lifecycle TEE</td><td>v1.0 / 2026-08-06</td></tr><tr><td>Intended audience</td><td>Users, partners, media, security questionnaires, and product pages</td></tr></tbody></table>

| Core commitment                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Plaintext source code exists only inside Minara-approved TEE workloads that have completed remote attestation. Ordinary services, hosts, databases, queues, logs, backups, and operations accounts do not touch plaintext. |

## 1. Formal external statement

### 1.1 Full version

Minara has deployed the full lifecycle of confidential strategy source code inside remotely attested hardware trusted execution environments (TEE). From encrypted browser upload, ciphertext storage, AI code processing, backtesting, paper trading, and live trading, to order intent output, source-code viewing, and execution receipt generation, plaintext source code exists only briefly inside approved TEE workloads. Ordinary APIs, workers, hosts, databases, caches, queues, logs, backups, and operations accounts cannot obtain plaintext source code.

Before upload, the user's browser verifies the TEE's remote attestation and approved measurement, then establishes a short-lived encrypted session with the enclave. The control plane only forwards ciphertext, artifact references, authorization tickets, and metadata that does not contain source code. Source code is encrypted with an independent DEK using AEAD. The storage layer keeps only ciphertext, wrapped DEK, context, and signed receipts. KMS encrypts key material to a designated enclave only when attestation, purpose, image, and policy conditions are all satisfied.

Strategy Studio, XStrategy, and AI tasks process source code in isolated TEE runtimes. Market data and required external dependencies enter through a controlled vsock proxy. Every output first passes through an in-enclave egress policy that applies default deny and minimization by purpose, destination, field, and size. The trading system receives only classified order intent. AI handles original source code only inside the enclave or through an attested confidential downstream. Ordinary model providers do not receive plaintext source code.

Every upload, view, AI processing task, or strategy execution generates a verifiable receipt bound to the artifact hash, input and output commitments, runtime measurement, policyVersion, purpose, time, and result status. If attestation fails, key policy does not match, or egress is denied, the system pauses or retries the task. It does not downgrade to a plaintext backend path.

### 1.2 Short version

| Statement                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Minara places the full lifecycle of strategy source code, from encrypted upload, ciphertext storage, AI, backtesting, and trading runtime to source-code delivery, inside remotely attested TEEs. Ordinary services and operations staff do not touch plaintext source code. Keys are released according to attestation, output is minimized through an egress gate, and every major operation receives a verifiable receipt. |

### 1.3 Product prompt copy

Full-lifecycle TEE is enabled: source code is decrypted and processed only inside verified confidential execution environments. You can view the measurement, strategy version, and execution receipt on the client. If attestation fails, the system fails closed and does not fall back to plaintext processing.

### 1.4 Media one-liner

Minara uses remote attestation, attested key release, ciphertext-only storage, TEE runtimes, and verifiable receipts to provide full-lifecycle confidential computing for strategy source code across upload, AI, backtesting, trading, and delivery.

## 2. Architecture for full-lifecycle TEE

<figure><img src="../.gitbook/assets/strategy-confidentiality-tee-architecture.png" alt="Minara full-lifecycle TEE public architecture, showing separation between the control plane and the attested confidential data plane"><figcaption><p>Figure 1 - The control plane is separated from the attested confidential data plane. Plaintext exists only inside the approved TEE pool.</p></figcaption></figure>

### 2.1 Three core boundaries

| Boundary                 | Responsibilities                                                                                                  | Explicitly does not touch                                |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| User side                | Verify attestation, establish an encrypted session, locally decrypt the source-code envelope, and verify receipts | Platform internal keys and other users' data             |
| Control plane            | Identity, owner, purpose, job, artifact ref, policy tickets, status, and classification results                   | Source code, DEK, debug plaintext, and raw AI context    |
| TEE data plane           | Decryption, validation, AI, backtesting, paper/live, egress decisions, rewrapping, and signed receipts            | Unapproved network destinations and unclassified output  |
| Ciphertext storage / KMS | Store ciphertext and wrapped DEK; release keys according to RecipientAttestation conditions                       | Plaintext source code and ordinary KMS Decrypt plaintext |

## 3. From upload to execution receipt

<figure><img src="../.gitbook/assets/strategy-confidentiality-tee-lifecycle.png" alt="Full-lifecycle TEE path from upload to execution receipt, with seven steps and fail-closed invariants"><figcaption><p>Figure 2 - Full-lifecycle TEE path and fail-closed invariants.</p></figcaption></figure>

### 3.1 Seven-step protection chain

1. Attestation verification: the client or task scheduler first verifies the approved measurement, signature chain, nonce, time, and policy version.
2. Encrypted upload: the browser establishes a short-lived ECDH session with the TEE, then uploads the source code, operation, and context in an AEAD envelope.
3. Ciphertext write: the TEE validates the source code and generates a DEK. It writes only ciphertext, wrapped DEK, context, and receipt.
4. Key release after attestation: the TEE runtime requests KMS with RecipientAttestation. If the conditions are not met, no usable key is returned.
5. Confidential execution: AI, backtesting, and paper/live run inside independent TEE pools. State and checkpoints are encrypted again before persistence.
6. Controlled output: the egress gate outputs minimal order intent, results, or browser-session envelopes according to destination and field allowlists.
7. Verifiable receipt: the result is bound to measurement, artifact/input/output hash, policy, purpose, time, and status, then signed.

## 4. What this means for users

| Scenario               | Full-lifecycle TEE behavior                                                                                                       | Protection for the user                                                              |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Upload                 | The browser verifies the TEE identity before encryption. The control plane only forwards ciphertext.                              | Ordinary APIs or proxies cannot read source code on the upload path.                 |
| Storage                | Databases, object storage, caches, and backups store only ciphertext and required metadata.                                       | Database snapshots and backups do not contain plaintext source code.                 |
| Backtesting            | Pine and XStrategy runtimes decrypt and execute inside attested enclaves.                                                         | Hosts and ordinary workers do not read source code.                                  |
| Paper/live             | Strategy state and checkpoints are encrypted inside the TEE. Orders are output only as minimal intent.                            | Trading services do not receive source code. They only process controlled actions.   |
| AI                     | Raw source code goes only to a local TEE model or an attested confidential downstream.                                            | Ordinary third-party model providers do not receive plaintext source code.           |
| Source-code viewing    | The TEE rewraps source code to a verified browser session. The client decrypts locally.                                           | Ordinary backends do not return plaintext source code in HTTP responses.             |
| Clone / public release | Cloning is completed inside the TEE. Public release requires explicit owner authorization and creates a separate public artifact. | Public release does not automatically expose private versions or historical context. |
| Operations / emergency | Break-glass runs only inside the TEE, requires two-person approval, MFA, and a short TTL, and issues a receipt.                   | Administrators cannot export source code to ordinary terminals or logs.              |

### 4.1 Verifiable evidence rather than commitments alone

1. The client verifies the AWS Nitro attestation certificate chain, COSE\_Sign1, nonce, public\_key, time, and approved PCRs.
2. The KMS policy constrains ImageSha384/PCR0, signing certificate/PCR8, environment, and encryption context.
3. The measurement registry supports active, grace, and revoked states. Client policy and KMS policy are updated together.
4. Execution receipts can be publicly verified, but they do not contain source code, DEK, or full sensitive inputs.
