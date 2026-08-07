# TEE-based Data Security

Your strategy source code is encrypted in your browser before it leaves your device, and it is decrypted only inside a hardware-attested trusted execution environment (TEE). Minara runs the complete lifecycle this way: upload, storage, AI processing, backtesting, paper trading, live trading, order output, source-code viewing, and receipt generation. Plaintext source code lives in enclave memory for the duration of an approved task and is never written to disk. It is not available to Minara's general infrastructure (API services, workers, hosts, databases, caches, queues, logs, and backups) or to Minara staff.

Minara's enclaves run on AWS Nitro Enclaves. Attestation, key release, and network egress are enforced by the platform, not by application code. Every check fails closed: when a condition is not met, the task stops instead of falling back to a path that would handle your code in plaintext.

### Encryption before upload

Your browser verifies the enclave's remote attestation document and confirms that its measurement matches an approved build. It then opens a short-lived encrypted session (ECDH) with the enclave and uploads your source code in an authenticated-encryption (AEAD) envelope. Minara's control plane forwards only ciphertext, artifact references, authorization tickets, and metadata that contains no source code.

### Storage

Each artifact is encrypted with its own data key. The storage layer holds the ciphertext, the wrapped data key, context, and signed receipts, and nothing else. AWS KMS releases key material to a designated enclave only when attestation, purpose, enclave image, and policy conditions are all satisfied. A decrypt call made from outside an enclave returns nothing usable.

### Processing

Strategy Studio, multi-asset strategy runs, and AI tasks each execute in isolated enclave runtimes. Market data and required external dependencies reach them through a controlled host proxy over vsock. An in-enclave egress policy checks every output, denies by default, and releases the minimum the destination needs. The trading system receives the resulting order intent and not the logic behind it. AI processing of your source code happens inside the enclave, and third-party model providers do not receive it in plaintext.

### Verifiable receipts

Every upload, view, AI task, and strategy execution produces a signed receipt. A receipt binds the artifact hash, input and output commitments, the runtime measurement, the policy version, the purpose, and the result. You can check a receipt yourself instead of taking our word for it.&#x20;

### Architecture

<figure><img src="../.gitbook/assets/image (136).png" alt=""><figcaption><p>The control plane never handles plaintext. Strategy source code is decrypted only inside attested enclaves.</p></figcaption></figure>

#### Where your code can and cannot go

| Layer                     | What it does                                                                                                      | What it never sees                                 |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| Your browser              | Verifies attestation, opens the encrypted session, decrypts your source code locally, checks receipts             | Minara's internal keys, other users' data          |
| Control plane             | Identity and ownership, task orchestration, artifact references, policy tickets, status, classification results   | Source code, data keys, AI prompts and context     |
| Enclave data plane        | Decryption, validation, AI, backtesting, paper and live trading, egress decisions, re-encryption, receipt signing | Unapproved network destinations, unfiltered output |
| Encrypted storage and KMS | Stores ciphertext and wrapped data keys; releases keys only against a valid enclave attestation                   | Plaintext source code                              |

### From upload to execution receipt

<figure><img src="../.gitbook/assets/image (163).png" alt=""><figcaption><p>Each step verifies the one before it. A failed check stops the task instead of opening a plaintext path.</p></figcaption></figure>

1. **Attestation.** The client or task scheduler verifies the enclave's approved measurement, signature chain, nonce, timestamp, and policy version before anything is sent.
2. **Encrypted upload.** The browser opens a short-lived ECDH session with the enclave and uploads the source code, operation, and context inside an AEAD envelope.
3. **Ciphertext write.** The enclave validates the source code, generates a data key, and persists only ciphertext, the wrapped key, context, and a receipt.
4. **Attested key release.** The enclave requests key material from KMS with its attestation document attached. Without a matching attestation, no usable key is returned.
5. **Confidential execution.** AI, backtesting, and paper and live trading run in separate enclave pools. Intermediate state and checkpoints are re-encrypted before they are persisted.
6. **Controlled output.** The egress gate emits only order intent, results, or a session envelope for your browser, according to destination and field allowlists.
7. **Signed receipt.** The outcome is bound to the runtime measurement, artifact and input and output hashes, policy, purpose, time, and status, then signed.

If attestation fails, a key policy does not match, or an egress request is denied, the task pauses or retries. There is no plaintext fallback path.
