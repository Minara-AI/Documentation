# Training methods

DMind's models combine two original training methods (HPS and C³-SFT) with standard methods like SFT, RLHF, LoRA, and distillation. This page covers each one briefly and notes which model uses what.

## Base models

<table><thead><tr><th width="98.546875">Series</th><th width="96.9140625">Parameters</th><th width="158.96484375">Base</th><th width="96.515625">Base provider</th><th>Role</th></tr></thead><tbody><tr><td>DMind-1</td><td>33B</td><td>Qwen3-32B</td><td>Alibaba</td><td>Web3 expert model for DeFi, tokenomics, governance, and smart contract Q&#x26;A and reasoning.</td></tr><tr><td>DMind-1</td><td>15B</td><td>Qwen3-14B</td><td>Alibaba</td><td>Lightweight distilled version of DMind-1. Suits low-latency real-time Q&#x26;A, on-chain analysis, and lightweight agents.</td></tr><tr><td>DMind-2</td><td>107B</td><td>GLM-4.5-Air</td><td>Zhipu</td><td>Flagship crypto investment analysis model. Covers macro trends through on-chain behavior, for professional advisory and institutional analysis.</td></tr><tr><td>DMind-2</td><td>4B</td><td>Qwen3-4B-Thinking-2507</td><td>Alibaba</td><td>Lightweight crypto investment analysis model for local and edge deployment, privacy, and low-latency use.</td></tr><tr><td>DMind-3</td><td>21B</td><td>gpt-oss-20b</td><td>OpenAI</td><td>Cloud and enterprise-VPC macro strategy finance engine for systemic risk, cross-chain narratives, institutional research, and agent orchestration.</td></tr><tr><td>DMind-3</td><td>4B</td><td><a href="https://huggingface.co/Qwen/Qwen3.5-4B">Qwen3.5-4B</a></td><td>Alibaba</td><td>Local financial modeling and strategy reasoning model. Privacy-first, available offline, with on-device deep reasoning.</td></tr><tr><td>DMind-3</td><td>270M</td><td><a href="https://huggingface.co/google/functiongemma-270m-it">functiongemma-270m-it</a></td><td>Google</td><td>On-device wallet and DEX intent recognition and function calling. Supports SEARCH_TOKEN and EXECUTE_SWAP, multi-chain, and Chinese/English intents.</td></tr></tbody></table>

Using DMind models requires honoring both DMind's Model Agreement and the underlying base model's original license.

## Standard methods

### Supervised fine-tuning (SFT)

The baseline method. Pair questions with reference answers and train the model to match. DMind-1's first training stage uses SFT.

### LoRA (Low-Rank Adaptation)

A parameter-efficient way to do SFT. Instead of updating all of the model's parameters, LoRA adds a small pair of low-rank matrices to each layer and trains only those. This cuts training cost by an order of magnitude or more. DMind-1 uses LoRA for SFT. The benchmark paper's controlled experiments also use LoRA with rank 16 and alpha 32.

### RLHF and PPO

Reinforcement Learning from Human Feedback. First, train a reward model on human preference data (answer A is better than answer B for this question). Then use that reward model as a training signal to optimize the main model with PPO (Proximal Policy Optimization), the same technique used to turn GPT-3 into ChatGPT. DMind-1's second training stage uses this pair.

### Knowledge distillation

A small student model learns from a large teacher model. DMind-1-mini is distilled from a dual teacher: DMind-1 itself plus a general SOTA model (run through DMind's DeepResearch framework to align its outputs to Web3 contexts). The distillation works at three levels. The student matches the teacher's final outputs, matches the teacher's full probability distribution over each token, and aligns intermediate-layer representations.

## DMind's two original methods

### HPS (Hierarchical Predictive Synthesis)

The training objective behind DMind-3 (21B). HPS teaches the Oracle to reason across a layered structure of inputs. At the bottom are raw on-chain events such as specific transactions and contract calls. In the middle are aggregated market indicators. At the top are macro signals such as Fed policy, CPI, and geopolitical events.

For each input modality, the model learns to predict the next global market state. The training loss combines a multi-modal weighted log-likelihood with a regularization term that penalizes drifting too far from the base model's parameters. The regularization is there to prevent catastrophic forgetting, so the model can specialize in finance without losing its general language ability.

HPS also gives the Oracle a two-mode inference toggle. Standard mode returns a direct answer. A special `[STRATEGY]` token switches the model into strategic mode, where it additionally considers risk paths and retrieves historically similar scenarios before answering. Fast and slow thinking, controlled by the caller.

### C³-SFT (Contrastive Chain-of-Correction SFT)

The training method behind DMind-3-Mini (4B). C³-SFT is built around one problem. A small model that confidently states something wrong is more dangerous than one that admits uncertainty.

Standard SFT trains a model to produce a correct answer given a question. C³-SFT changes the training data into four-step chains. The chain starts with the question, then an initial answer that is plausible but flawed, then an explicit critique that identifies what the initial answer missed (for example, an oracle manipulation risk that was not considered), then a corrected answer that addresses the critique.

The model learns to produce all four steps. At inference time, this turns into the self-questioning behavior. The model gives an initial answer, critiques itself, and revises. The "contrastive" part of the name comes from showing the model both correct and typical-wrong answers during training, so it learns the specific shape of the failure modes.

This is a lightweight version of the System-2 reasoning approach that larger models implement with separate thinking tokens. Putting it directly into a 4B model is what lets Mini run on a user's device while keeping a safety net.

## Training data

DMind-1's training data is 13,276 expert-curated knowledge items, distilled from 32.7GB of Web3 source documents across DeFi, tokenomics, governance, smart contracts, Layer-1/2 architecture, NFTs, DAOs, and security.

DMind-3's training data is larger and more structured:

| Source                       | Share | What it is                                                                                           |
| ---------------------------- | ----- | ---------------------------------------------------------------------------------------------------- |
| Institutional alpha research | 35%   | Crypto-native fund and TradFi reports, decomposed through a causal model                             |
| Global macroeconomic data    | 25%   | Time series from FRED, World Bank, IMF, joined with on-chain indicators                              |
| Cross-chain index data       | 20%   | Full transaction, state, and log history across major EVM chains, Solana, Cosmos                     |
| Post-mortems and audits      | 10%   | Systemic failures, economic attacks, protocol hacks, with focus on early signals and contagion paths |
| Geopolitics and regulation   | 10%   | Global regulatory changes, policy proposals, geopolitical events affecting digital assets            |

Total: 500,000+ curated documents, plus multi-terabyte on-chain structured data.

All training data is reviewed by domain experts rather than scraped. The selection criteria are published in the model cards and papers.
