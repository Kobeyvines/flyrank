# Week 3 — Content Map & Identity Kit

## One-line claim

**I build ML systems that go from raw data to deployed decisions — not just a notebook.**

I tested nine other versions of this before landing here. The others either buried the gap I
actually close (notebook vs. production — which is exactly what my churn audit is about), or
drifted toward implying causation I can't back up. This one names the deliverable, points at the
gap, and stays inside what I can actually defend in an interview.

---

## Content map

Every page ladders up to one action: inspecting my repo on GitHub. That CTA lives in the header
on every page, so it's always one click away — the page-level CTAs below are secondary paths
into the same destination.

### Home
1. **Hero** — my one-line claim, plus one sentence on what "grounded, observational" means in practice.
2. **Featured case** — a short teaser on the churn audit: the misalignment, the accuracy collapse, two or three sentences, no more.
3. **Proof snapshot** — two or three bullets, each one I could defend line-by-line in an interview. Nothing adjacent, nothing padded.
- Primary CTA: *Inspect the repo →*
- Secondary CTA: *Read the full audit →*

### Work / Case Studies
1. **Churn Prediction Model Audit** (lead project, full write-up) — misaligned data and retention teams, the audited accuracy collapse (reported vs. production), precision degradation, and a tiered intervention recommendation. I'm explicit that implementation was out of my scope.
2. **Second case study** — not built yet. Until it exists, this page stays single-case rather than padded with something half-finished.
- CTA per case: *View the repo →* — one CTA, not a stack of competing links.

### Method (replacing About)
1. **How I audit** — the actual process behind the churn case: how I find the misalignment, how I measure the collapse, why I stop at recommendations instead of implementation.
2. **The guardrail** — why I don't claim causation. This is a proof-statement line, not a personality paragraph.
- CTA: *See the method applied →* (loops back to the case study, not a dead end)

### Contact
1. Email address, one sentence on the kind of inquiry I want — technical leads and hiring managers, specifically.
- CTA: *Email me*

### What I still need to gather
- A real screenshot of the reported-vs-production accuracy comparison
- A real screenshot or chart of the precision-degradation finding
- My GitHub repo URL confirmed live, with a README that holds up on its own
- The exact accuracy numbers behind "the collapse" — I'm currently gesturing at this, and it needs real figures before it ships
- A decision on whether a second case study is coming, so the Work page section count is honest
- My contact email, confirmed

---

## Identity kit

**Type:** IBM Plex Sans for headings and my name, Inter for body copy. Two fonts, not a pile.

**Palette:**
- Text `#1A1A1A`
- Background `#FAFAFA`
- Accent `#2D5FE0` — links and CTAs only
- Divider `#E4E7EC` — quiet, does almost no visual work on purpose

I chose blue over green specifically because green reads as generic growth-SaaS, and my whole
positioning is built on finding where something broke — that's not a "green" story.

**Mark:** a "KV" monogram in the accent color. I checked it at favicon size (32px) and it still
reads clean.

**Style note** (pasted into my Claude Project's custom instructions):
> IBM Plex Sans (600) for headings and the KV mark, Inter (400) for body — text #1A1A1A on
> background #FAFAFA, one accent #2D5FE0 for links and CTAs only.
> Calm and audit-grade: the work is the loudest thing on the page, never the frame around it.
