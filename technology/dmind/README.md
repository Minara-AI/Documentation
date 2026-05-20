# DMind

Minara is powered by [DMind](https://dmind.ai/), an open-source research organization building large language models, benchmarks, datasets, and tools for Web3 and digital finance. DMind's models handle the finance-native parts of Minara: parsing on-chain data, reasoning about DeFi protocols, evaluating risk in transactions, and generating market research. These models are paired with general-purpose models such as Claude and GPT, which handle the tasks that fall outside finance.

## Why a domain-native model

General-purpose LLMs have four structural gaps in Web3.

Web3 content is underrepresented in their training data, so they often invent plausible but wrong answers about specific protocols, contract mechanics, or token economics. Cloud-only inference forces users to send wallet activity and trading intent to third-party servers. Chat-based products provide no help at the moment that matters most, which is when a user signs a transaction. And API round-trips are too slow for time-sensitive scenarios such as liquidations or MEV protection.

DMind builds models that close these gaps, with weights and training data published openly so anyone can audit them.

## What DMind ships

DMind has released seven open-source models across three generations, ranging from a 270M-parameter on-device safety model to a 21B cloud reasoning model. Alongside the models, DMind publishes an evaluation suite for Web3 understanding (1,917 expert-reviewed questions across 9 sub-domains, accepted to KDD 2026), and a TypeScript SDK for integrating DMind models into Web3 applications.

## How DMind powers Minara

Minara routes work across DMind's models based on what each task needs.

Transaction-time safety checks run on a small on-device model (DMind-3-Nano), so they work without a network round-trip. Strategy analysis and private research run on a local 4B model (DMind-3-Mini) that reasons about a user's specific holdings without sending them to the cloud. Market-wide research, cross-chain analysis, and long-form reports run on the 21B Oracle model in the cloud, which has a 256k context window and aggregates global data.

The split is not arbitrary. It is the [sovereign architecture](sovereign-architecture.md) that defines what runs where, and why.

{% hint style="info" %}
The final go/no-go decision on a transaction always happens on the user's device, never in the cloud. This is the safety anchor of the entire architecture.
{% endhint %}

## Read next

* [Sovereign architecture](sovereign-architecture.md). The Edge-Local-Cloud design behind DMind-3 and what it means for privacy.
* [Model family](model-family.md). What each of the seven models does and when it gets used.
* [DMind Benchmark](benchmark.md). The Web3 evaluation suite accepted to KDD 2026.
* [Training methods](training-methods.md). HPS, C³-SFT, and how the models are taught Web3-specific reasoning.

## Resources

* Website: [dmind.ai](https://dmind.ai/)
* GitHub: [github.com/DMindAI](https://github.com/DMindAI)
* Hugging Face: [huggingface.co/DMindAI](https://huggingface.co/DMindAI)
* Papers: [DMind Benchmark (arXiv:2504.16116)](https://arxiv.org/abs/2504.16116), [DMind-3 (arXiv:2602.11651)](https://arxiv.org/abs/2602.11651)
