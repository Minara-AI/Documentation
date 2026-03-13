# Personalization

### Overview

Personalization is Minara’s context-aware AI layer that adapts analysis and decision support to each user’s unique habits and preferences.

Rather than generating generic answers, Minara gradually learns how you think, analyze markets, and make trading decisions, allowing the system to produce insights that better match your style and workflow.&#x20;

With user consent, Personalization continuously improves the relevance and consistency of Minara’s responses across features such as chat analysis, Trading Copilot, and strategy guidance.

The goal is simple:

> Make Minara feel less like a generic AI assistant and more like a financial partner that understands how you work.

***

### Why Personalization Matters

Financial decision-making is highly individual.

Two traders may look at the same market data but approach decisions differently:

* Some prefer fast momentum trades
* Some focus on long-term macro signals
* Some rely heavily on technical indicators
* Others prioritize portfolio allocation and risk control

Traditional AI assistants provide the same analysis to everyone.

Minara Personalization instead adapts to your analytical habits and decision patterns, producing responses that feel more aligned with how you normally operate. &#x20;

***

### Personalization Architecture

Minara’s personalization system is designed as a controllable and explainable layer, rather than a hidden behavioral model. All personalization modules are enabled by default, but users can disable them at any time.

It combines four key modules to build contextual understanding:

#### Trading Summary

<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

**Minara Wallet Context**

Minara incorporates the portfolio composition of your **Minara spot wallet** into analysis.

Instead of answering questions in isolation, the system can consider:

* assets you currently hold
* exposure concentration
* risk distribution
* unrealized positions

This allows insights to be contextualized to your current holdings.

> The context of Minara perpetual wallets is not yet integrated.&#x20;

**External Portfolio**&#x20;

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

You may also import your wallet addresses outside of Minara, and let Minara summarize your trading activity and patterns.

This includes observations such as:

* typical holding time
* preferred trading pairs
* strategy patterns
* performance tendencies

These summaries allow Minara to better understand your decision-making behavior through a broader portfolio context.



#### Custom Prompt

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

Custom Prompt allows users to define their own system-level instructions for how Minara should respond.

Similar to custom prompts in other LLM products, this feature lets you guide Minara’s behavior, tone, and analytical focus. The instructions you provide will be applied to your interactions with Minara, helping the AI better align with your preferred workflow.

Users may use Custom Prompt to specify:

* preferred analysis style or depth
* trading frameworks or indicators to prioritize
* response format (e.g., concise summary vs detailed breakdown)
* specific assets, markets, or strategies to focus on
* personal preferences such as Minara’s tone and how you would like to be addressed



#### Tags

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

Tags represent structured dimensions of your user profile that help Minara better understand your preferences, habits, and trading style.

Each dimension corresponds to a set of possible labels. For example:

* Risk Profile: Aggressive / Balanced / Conservative
* Decision-Making Style: Data-Driven / Narrative-Driven / Community-Driven / Tech-Driven
* Trading Frequency: Passive Holder / Market Watcer

Minara may automatically infer and update these tags based on your conversations and interactions over time.

You can also manually modify any tag. Once a tag is manually set, it will not be automatically overwritten by AI. If a tag does not apply, you may choose N/A.

These tags allow Minara to adjust analysis, suggestions, and explanations to better match your individual profile.

#### Memories

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

Important information about your preferences, strategies, and interactions that Minara stores over time.

Examples include:

* preferred trading timeframe
* preferred analysis style
* typical risk tolerance

These memories help Minara maintain continuity across conversations. You may also delete memorries that you do not want Minara to keep.

