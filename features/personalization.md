# Personalization

Minara's personalization system adapts analysis and responses to your trading habits, portfolio context, and stated preferences. Rather than returning the same generic output to every user, Minara uses information you provide and patterns it observes over time to make responses more relevant to how you actually work.

All personalization modules are enabled by default. You can disable any of them at any time.

## Where to find personalization settings

Click your avatar in the top-left corner of the app and select **Personalization** from the profile menu. The sections below (Trading summary, Custom Prompt, Tags, and Memories) each appear as separate panels on that page.

<!-- IMAGE: 建议命名 personalization-menu-location.png
     内容：app 左上角 avatar 菜单展开，Personalization 项高亮
     alt text 建议：Account menu opened from the avatar in the top-left with the Personalization option highlighted
     VERIFY: 确认菜单里 entry 叫 "Personalization"，以及入口是 avatar 下拉还是 Settings 子页 -->

***

## Trading summary

### Minara wallet context

<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

Minara incorporates your Minara spot wallet holdings into its analysis. When you ask market questions, Minara can factor in:

- The assets you currently hold
- Your exposure concentration
- Risk distribution across the portfolio
- Unrealized positions

This means analysis is relative to your current situation, not answered in isolation.

The context of Minara perpetual wallets is not yet integrated.

### External portfolio

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

You can import wallet addresses outside Minara. Minara summarizes your trading activity across those wallets, including:

- Typical holding duration
- Preferred trading pairs
- Observed strategy patterns
- Historical performance tendencies

This gives Minara a broader picture of how you trade, beyond what happens inside the platform.

***

## Custom prompt

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

Custom Prompt lets you write system-level instructions that apply to all your Minara interactions. Use it to specify:

- Preferred analysis depth or style
- Indicators or frameworks you want Minara to prioritize
- Response format (concise summary vs. detailed breakdown)
- Assets or markets to focus on
- Tone and how you want Minara to address you

These instructions persist across sessions and take precedence over default behavior.

***

## Tags

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

Tags represent structured dimensions of your trading profile. Each dimension has a set of possible labels. Examples:

- **Risk profile:** Aggressive / Balanced / Conservative
- **Decision-making style:** Data-Driven / Narrative-Driven / Community-Driven / Tech-Driven
- **Trading frequency:** Passive Holder / Market Watcher

Minara may automatically infer and update tags based on your conversations over time. You can also set any tag manually. Once a tag is manually set, Minara will not overwrite it automatically. If a tag does not apply to you, set it to N/A.

Tags help Minara calibrate how it frames analysis, suggestions, and explanations.

***

## Memories

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

Memories are specific facts Minara stores about your preferences, strategies, and past interactions. Examples:

- Preferred trading timeframe
- Preferred analysis approach
- Typical risk tolerance

Memories allow Minara to maintain continuity across conversations — you do not need to re-explain your context each time. You can delete any memory you do not want Minara to retain.
