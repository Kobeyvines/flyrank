# Prompt Iteration Log — FL-01

**Task (real, from my ML track):** Explain to a non-technical marketing stakeholder why `search_volume` should not be treated as a performance outcome in a Lane 1 ranking-signal analysis — it's a demand/context variable, not a measure of how well content is doing. This comes up for real: stakeholders who trust SEO tools by default keep citing high search volume as proof a page is "doing well," which conflates *demand for a topic* with *how the page is performing against that demand*.

---

## Version 0 — Naive baseline (pre-track)

**Prompt:**
> "Explain search volume."

**Output (representative excerpt):**
> "Search volume refers to the number of times a keyword is searched over a given period, usually reported monthly. It's a metric used in SEO and keyword research to gauge interest in a topic. Higher search volume generally indicates more potential traffic. Tools like Google Keyword Planner, Ahrefs, and SEMrush report this metric."

**What this reveals:** It answers "what is search volume," not the actual question — it doesn't touch the misconception at all, because I never stated one. This is a textbook definition, useless in the actual stakeholder conversation.

---

## Version 1 — Role assignment

**Technique:** Assign the model a specific expert role with a stance.

**Prompt:**
> "You are a senior data scientist reviewing content performance with a marketing stakeholder who currently believes high search volume proves a page is performing well. Explain why that belief is a mistake."

**Output (representative excerpt):**
> "High search volume tells you how many people are searching for a topic — it says nothing about whether your specific page is capturing that demand. A page can sit on a high-volume keyword and still perform poorly if it ranks low, has weak click-through, or provides a bad experience. Treating volume as a performance signal confuses the size of the opportunity with your success at capturing it."

**What actually improved:** The output stopped defining the term and started making an argument — it directly named the confusion (opportunity size vs. capture rate) instead of describing the metric neutrally. Assigning a role with a stance ("explain why that belief is a mistake") is what did this, not just "senior data scientist."

**What still failed:** It's still written like an internal note to another analyst, not something you'd say out loud to a stakeholder who's about to push back defensively.

---

## Version 2 — Context and motivation

**Technique:** Add the real situational stakes — why this correction needs to happen and what's at risk if it doesn't land.

**Prompt:**
> [Same as V1, plus:] "Context: this stakeholder has flagged a page as a 'success story' in a report to leadership because it targets a high-volume keyword, but the page's actual clicks and position are weak. If this framing goes unchallenged, the team will keep chasing high-volume keywords and ignore pages that are quietly underperforming. Explain this so the correction lands without the stakeholder feeling attacked."

**What actually improved:** The tone shifted noticeably — it opened with an acknowledgment ("It makes sense that a high-volume keyword feels like a win") before pivoting to the correction, and it tied the explanation to a consequence that matters to the stakeholder ("the team could keep investing in the wrong pages"). Context about *stakes* changed the argument from abstract to consequential — it now had a reason to exist beyond being technically correct.

**What still failed:** It still didn't give the stakeholder anything to check for themselves — no concrete question they could ask next time before calling a page a success.

---

## Version 3 — Few-shot examples

**Technique:** Show the model one example of the tone/pattern I want, so it can match the shape rather than guess it.

**Prompt:**
> [Same as V2, plus:] "Here's the tone I want — match this pattern: 'It's easy to assume a fast car wins races, but speed alone doesn't matter if it runs out of gas before the finish line. The question isn't how fast the car *can* go, it's whether it actually crosses the line.' Use a comparably concrete, non-technical analogy for search volume vs. performance."

**What actually improved:** It produced an analogy of its own instead of an abstract explanation: "Search volume is like the size of the crowd walking past a store window — it tells you how many people *could* look in, not how many actually stopped and bought something. A packed street doesn't guarantee sales; it means the opportunity is there, waiting to be captured or missed." This is the first version I could hand to a stakeholder verbatim.

**What still failed:** The analogy is strong, but it still doesn't point back to what to look at instead — it explains the flaw in the belief without redirecting toward the fix.

---

## Version 4 — Output structure

**Technique:** Specify an explicit shape for the answer.

**Prompt:**
> [Same as V3, plus:] "Structure the answer in exactly three parts: (1) the analogy, (2) the specific mistake in one sentence, (3) the one metric to look at instead and why."

**What actually improved:** For the first time, the output ends somewhere useful instead of just correcting a mistake and stopping: "(3) Look at click-through rate and average position instead — those tell you whether the page is actually capturing the demand that search volume shows exists." Forcing a structure with a mandatory third part is what produced the redirect that V2 and V3 were both missing.

**What still failed:** Minor — part (2), "the specific mistake in one sentence," sometimes ran two sentences. The instruction "in one sentence" wasn't strictly obeyed, which is a small but real signal that length constraints inside a structure aren't automatically enforced just because they're stated.

---

## Version 5 — Step decomposition

**Technique:** Break the task into explicit sequential steps rather than one instruction.

**Prompt:**
> "Do this in order: (1) Restate the stakeholder's current belief in one sentence, so they recognize it as their own claim. (2) Give one concrete, non-technical analogy for why that belief is incomplete. (3) State the specific mistake in exactly one sentence. (4) Name the one metric to check instead, and explain in one sentence why it answers the real question. Context: [same as V2]. Role: [same as V1]."

**What actually improved:** Splitting the task into ordered steps fixed V4's leftover problem — step (3) now reliably held to one sentence, because the model was tracking discrete steps rather than a bundled paragraph with an embedded length rule. It also added something new and genuinely useful: opening with the stakeholder's own belief restated back to them ("You're reading the page's high search volume as proof it's succeeding") — which primes agreement before the correction, rather than opening with the correction itself.

**What still failed:** Nothing broke, but the output is now noticeably more mechanical/checklist-like in feel — you can sense the four steps as four steps rather than one flowing explanation. For a live conversation, a human would still smooth the seams between steps before saying it out loud.

---

## Cross-Model Comparison

**Final prompt used (see template below) run on Claude — actual output:**
> "You're reading this page's high search volume as proof it's succeeding — and it's easy to see why. But search volume is like the size of a crowd walking past a store window: it tells you how many people *could* look in, not how many actually stopped and bought something. The mistake is treating the size of the opportunity as if it were the result. To answer the real question, look at click-through rate and average position instead — those show whether the page is actually capturing the demand that the search volume proves exists."

**ChatGPT output:**

> **1. Your current belief:** “If a page has high search volume, that means the page is performing well.”
>
> **2. Analogy:** A shop being on a busy street doesn’t mean it’s successful—lots of people may pass by, but what matters is how many actually walk in and buy something.
>
> **3. The specific mistake:** You’re treating search volume as evidence of performance, when it only measures the size of the potential audience.
>
> **4. What to check instead:** Compare impressions, clicks, CTR, and average ranking position for the page, because that shows whether the page is actually capturing the demand it has access to.

**Predicted comparison (labeled as prediction, not verified):**
Based on commonly documented differences rather than this specific run: ChatGPT tends to answer step-decomposition prompts with more visible numbered/bulleted formatting even when asked for flowing prose, while Claude tends to fold the same steps into continuous sentences unless a rigid format is explicitly forced. ChatGPT also tends to add a short unprompted summary line at the end ("In short, ...") that wasn't requested by any of the five techniques above. Neither of these is a quality judgment — they're formatting defaults, and either could be corrected with the "output structure" layer alone.

**Action required to complete this deliverable honestly:** run the final template on ChatGPT, replace the placeholder above with the real output, and rewrite the "predicted comparison" section as an actual comparison — noting specifically where tone, accuracy, structure, or failure points genuinely diverged.

---

## Final Reusable Template

> "You are [ROLE] explaining [TOPIC] to [SPECIFIC AUDIENCE], who currently believes [THE MISCONCEPTION]. Context: [WHY THIS MATTERS RIGHT NOW / WHAT'S AT STAKE IF THE MISCONCEPTION GOES UNCORRECTED]. Do this in order: (1) Restate their current belief in one sentence, so they recognize it as their own claim. (2) Give one concrete, non-technical analogy for why that belief is incomplete. (3) State the specific mistake in exactly one sentence. (4) Name the one thing to check or do instead, and explain in one sentence why it answers the real question."

**Why this combination survived:** role + context earned their place by giving the explanation a stance and stakes instead of a neutral definition (V1–V2). The few-shot analogy example earned its place by giving the model a concrete pattern to match instead of guessing at "non-technical" (V3). Step decomposition survived over plain output-structure because it was the only version that actually enforced the one-sentence constraints it stated (V4 vs. V5).

---

## Summary Table

| Version | Technique | Net effect |
|---|---|---|
| V0 | — (naive) | Neutral definition, doesn't address the real misconception |
| V1 | Role assignment | Shifted from definition to argument with a stance |
| V2 | Context and motivation | Added stakes; softened tone to avoid stakeholder defensiveness |
| V3 | Few-shot examples | Produced a genuinely usable, concrete analogy |
| V4 | Output structure | Added the missing "what to do instead" — but didn't enforce its own length rule |
| V5 | Step decomposition | Fixed V4's length-rule miss; primed agreement before correction; slightly more mechanical feel |
