# DMind Benchmark

DMind Benchmark is an evaluation suite for Web3 understanding in large language models. It was accepted to the KDD 2026 Datasets & Benchmarks Track out of 513 submissions (acceptance rate around 29%), and will be presented at the main conference in Jeju, South Korea, in August 2026.

The dataset is open and has been downloaded over 13,000 times from Hugging Face. It is the most-used artifact in the DMind ecosystem.

## What it covers

1,917 expert-reviewed questions across 9 Web3 sub-domains:

1. Fundamental blockchain concepts: hashing, Merkle trees, consensus, PoW/PoS, block structure, forks.
2. Blockchain infrastructure: Layer-1 vs Layer-2 (Optimistic vs ZK Rollups), bridges, node architecture, RPC.
3. Smart contracts: Solidity, call mechanics, storage, EVM bytecode, upgrade patterns.
4. DeFi mechanisms: AMM mathematics, lending rate models, liquidation logic, derivatives pricing.
5. DAOs: governance tokens, voting, proposals, quorum, timelocks.
6. NFTs: ERC-721/1155 standards, royalty mechanics, floor pricing, NFT lending.
7. Token economics: issuance, vesting, burning, incentive alignment, price discovery.
8. Meme concepts: crypto-specific cultural terms and meme-token dynamics.
9. Security vulnerabilities: reentrancy, flash-loan attacks, oracle manipulation, signature replay, common audit findings.

## Question formats

The benchmark uses two types of questions. Multiple choice questions test factual recall. Open-ended tasks include smart contract debugging, where the model has to find the vulnerability in a Solidity snippet, and on-chain numeric reasoning, where the model is given an AMM pool state and has to compute the profit from a specific attack vector.

The open-ended tasks are deliberately harder than multiple choice. A model can pattern-match its way through multiple choice. Numeric reasoning and code analysis require actually working the problem.

## What the paper found

The latest version of the benchmark has evaluated 31 mainstream large models, including GPT-5, Claude Sonnet 4.5, DeepSeek, Gemini, Grok, and the Qwen series. Three findings stand out.

### Fundamentals are mostly solved, depth is not

Every major model does reasonably well on blockchain fundamentals, the kind of content that appears on Wikipedia. Performance drops sharply on token economics, meme concepts, and security. These are the areas where Web3 expertise actually matters, and where general-purpose models tend to invent plausible-sounding but incorrect answers.

### Cost and accuracy do not move together

When you plot accuracy against per-token cost, there is a clear Pareto frontier. The GPT-5 series sits at the high-accuracy end. Some open models, including GPT-OSS-120B, Kimi K2, and Qwen3-235B Thinking, offer better value in the middle. A few well-known closed models turn out to be both expensive and weaker than alternatives on Web3 tasks specifically. The paper publishes the full data so the numbers can be reproduced.

### Fine-tuning on more data does not close the gap

The paper runs a controlled experiment. Take three base models (QwQ-32B, Qwen3-32B, DeepSeek-R1-Distill-Llama-70B), fine-tune each one on the full benchmark dataset with LoRA, and measure improvement. The learning curves stay shallow. Feeding more data does not unlock Web3 reasoning. The real bottleneck is multi-step inference, cross-concept association, and understanding a market that changes over time. This is the argument for new training methods rather than bigger training sets, and the reason DMind invested in HPS and C³-SFT (see [Training methods](training-methods.md)).

## Where to read it

* Paper: [arXiv:2504.16116](https://arxiv.org/abs/2504.16116)
* Dataset: [huggingface.co/datasets/DMindAI/DMind\_Benchmark](https://huggingface.co/datasets/DMindAI/DMind_Benchmark)
* KDD 2026 review: [OpenReview forum](https://openreview.net/forum?id=RvmxTg2mi5)
