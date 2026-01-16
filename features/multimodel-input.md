# Multimodel Input

## Personalization

Personalization is Minara’s AI layer that adapts chat responses to your preferences and context. It helps Minara deliver answers that are **more relevant, more consistent, and easier to act on.**

###

### **What you get**

With Personalization enabled, Minara can:

* **Match your decision style** (e.g., data-driven vs narrative-driven) and preferred **explanation depth**
* **Keep responses consistent** (structure, emphasis, risk checks, and tone)
* **Use high-level context** (when enabled) to avoid generic advice and reduce repeated back-and-forth

### **How it works**

Personalization only applies to the inputs you explicitly enable. When enabled, Minara uses them to shape **how responses are framed.**<br>

**Basic flow**

1. **Minara autaomaicalyl collect some from your usage** or you can **Inputs you control on "Personalization" Panel**(Tags, Memories, Trading Summary, Custom Prompt)
2. Minara converts them into a small set of **preference + context signals** (e.g., your decision style, risk posture, preferred depth)
3. Those signals guide the response: **structure, emphasis, depth, and risk checks**



**What it changes**

* The **structure** of the answer (e.g., thesis → levels → risk checks → next actions)
* Which **signals** are prioritized (based on your style and horizon)
* How **detailed** the explanation is (concise vs deep)
* How **risk** is presented (guardrails, invalidation, position sizing prompts)



### **How to use**

Go to **Settings → Personalization** and toggle each module on or off:



* **Tags** — structured preferences you can edit
* **Memories** — saved helpful info from chats (removable)
* **Trading Summary** — high-level context snapshot (optional / if available)
* **Custom Prompt** — your explicit response rules (optional)

<figure><img src="../.gitbook/assets/Screen Shot 2026-01-16 at 7.03.45 PM.png" alt=""><figcaption></figcaption></figure>



### Inputs

#### 1) Tags

Tags are **structured preferences.** Minara uses them to choose the right framing, depth, and emphasis in chat.&#x20;

* use the **dropdown** menus to set or update your preferences (example: Decision-Making Style)—things like decision-making style, risk profile, learning preference, and trading habits.&#x20;

<figure><img src="../.gitbook/assets/Screen Shot 2026-01-16 at 6.40.16 PM.png" alt=""><figcaption><p>Tags are editable. Use dropdowns to tune how Minara responds.</p></figcaption></figure>

#### 2) Memories (transparent and removable)

Memories store **useful, stable information from your chats** (e.g., language preference, frequently discussed topics). You can review and delete any memory at any time.

* click **Manage Saved Memories** to review and delete items you don’t want Minara to reference.

<figure><img src="../.gitbook/assets/Screen Shot 2026-01-16 at 6.42.02 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screen Shot 2026-01-16 at 6.42.07 PM.png" alt=""><figcaption></figcaption></figure>

***

#### 3) Trading Summary

Trading Summary is a **high-level snapshot** used to make chat more context-aware. It’s designed to be _summary-level_ (helpful for relevance) rather than exposing sensitive details.

<figure><img src="../.gitbook/assets/Screen Shot 2026-01-16 at 6.43.05 PM.png" alt=""><figcaption><p>Trading Summary provides a high-level context snapshot to improve relevance.</p></figcaption></figure>

#### 4) Custom Prompt

Custom Prompt lets you set **your own rules** for how Minara should respond.

If you want more predictable formatting or stricter rules, add a Custom Prompt. Keep it short and specific.

Suggested template:

* **Structure:** “Answer in: Summary → Key signals → Risk checks → Next actions.”
* **Style:** “Be concise. Use bullet points. Avoid long paragraphs.”
* **Safety:** “If uncertain, say what is unknown and what to verify.”



***

### 📌 Example Scenarios

Below are typical usage scenarios for Personalization. Users are free to explore beyond these examples.

For best results, we recommend enabling **Quality mode** when you want deeper reasoning and more thorough risk checks.

#### 🧭 Scenario 1 — “Make it match my decision style”

**Goal:** Get answers that fit how you decide (data-first vs narrative-first vs community sentiment vs tech-first).

**Setup**

* Turn on **Tags**
* Set **Decision-Making Style** (e.g., Data-Driven)

**Try this prompt**

> “Analyze BTC’s current setup. I’m Data-Driven — prioritize evidence, key levels, and invalidation conditions. End with a clear action plan.”

**What you’ll see**

* More structured logic, clearer levels, explicit invalidation, less storytelling.

***

#### 🧱 Scenario 2 — “Always give me a disciplined plan”

**Goal:** Avoid improvising off raw price moves by enforcing a consistent decision framework.

**Setup**

* Turn on **Custom Prompt**
* (Optional) Turn on **Tags** and set Risk Profile

**Custom Prompt example**

> “Always respond with: 1) Thesis 2) Key levels 3) Risk checks 4) Position sizing suggestion 5) Invalidation triggers 6) Next action.”

**Try this prompt**

> “I’m considering a SOL trade. Give me a disciplined plan using my structure.”

**What you’ll see**

* A repeatable template every time: fewer missed risk checks.

***

### Control & safety notes

* **Opt-in by default:** Nothing is used unless you enable it.
* **Editable:** Tags can be changed at any time.
* **Reversible:** Memories can be deleted; modules can be toggled off.
* **Bounded context:** Trading Summary is intentionally high-level, designed for relevance without oversharing.
