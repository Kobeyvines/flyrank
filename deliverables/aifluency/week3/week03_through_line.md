# Week 3 — The Through-Line

## One-line claim

**I build ML systems that go from raw data to deployed decisions — not just a notebook.**

I ran ten options through this test: does it name what I actually prove, without implying more
than the data can support? Most of the other nine either buried the real gap I close — notebook
versus production, which is the whole story of my churn audit — or drifted into language that
sounded like I was claiming causation. This one survives both checks, and I can say it out loud
in an interview without qualifying it.

---

## Content map

Every call to action on every page ladders up to one action: inspecting my repo on GitHub. That
CTA sits in the header on every page, so it's always available — the page-level CTAs below are
the secondary paths into the same destination.

### Home
1. **Hero** — my one-line claim, plus one sentence on what "grounded, observational" means in practice.
2. **Featured case** — a short teaser on the churn audit: the misalignment, the accuracy collapse. Two or three sentences, no more.
3. **Proof snapshot** — two or three bullets, each one I could defend line-by-line in an interview. Nothing adjacent to my actual work, nothing padded to look broader.
- Primary CTA: *Inspect the repo →*
- Secondary CTA: *Read the full audit →*

### Work / Case Studies
1. **Churn Prediction Model Audit** (lead project, full write-up) — leads because it's my strongest and most complete work. Covers the misaligned data and retention teams, the audited accuracy collapse (reported vs. production), precision degradation, and a tiered intervention recommendation. I'm explicit that implementation was out of my scope.
2. **Second case study** — not built yet. Until it exists, this page stays single-case rather than padded with something half-finished.
- CTA per case: *View the repo →* — one CTA per case, not a stack of competing links.

### Method (replacing About)
1. **How I audit** — the actual process behind the churn case: how I find the misalignment, how I measure the collapse, why I stop at recommendations instead of implementation.
2. **The guardrail** — why I don't claim causation. This is a proof-statement line, not a personality paragraph.
- CTA: *See the method applied →* (loops back to the case study, not a dead end)

### Contact
1. Email address, one sentence on the kind of inquiry I want — technical leads and hiring managers, specifically.
- CTA: *Email me*

---

## Still need to gather

- A real screenshot of the reported-vs-production accuracy comparison
- A real screenshot or chart of the precision-degradation finding
- My GitHub repo URL confirmed live, with a README that holds up on its own without me narrating it
- The exact accuracy numbers behind "the collapse" — I'm currently gesturing at this in draft copy, and it needs real figures before it ships
- A decision on whether a second case study is coming, so the Work page's section count is honest rather than aspirational
- My contact email, confirmed and tested
