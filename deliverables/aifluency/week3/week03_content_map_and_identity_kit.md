# Week 3 Deliverable — Content Map & Identity Kit

**Proof statement (the test every choice below is held against):**
> I demonstrate applied machine learning and search intelligence through grounded, observational
> data analysis — translating raw performance metrics into clear, actionable business
> decision-support tools without overclaiming causation.

**Assumption stated up front:** the content map below assumes your live sitemap is
**Home / Work (Case Studies) / Method / Contact**, per the four-page structure discussed
previously (About → Method rename, persistent GitHub CTA in header). Correct this if the real
structure differs — everything downstream depends on it being right.

---

## 1. One-line claim

Ten drafts, narrowed to five worth reading, one recommended. The choosing is yours — that's the
actual assignment, not the drafting.

1. I take messy data and ship ML systems that actually make it to production — not just the notebook.
2. I turn raw performance data into decisions your team can act on, not just a dashboard.
3. **I build ML systems that go from raw data to deployed decisions — not just a notebook.** *(recommended)*
4. I close the gap between a model that scores well and a system that decides well.
5. Raw data in, deployable decisions out — that's the ML system I build.

**Why #3:** it's the only one that does three things at once — names the deliverable (a deployed
system, not a report), implies the gap it closes (notebook vs. production, which is your churn
audit's whole story), and stays inside the causation guardrail. It's also short enough to survive
being read on a phone in three seconds.

**Your call:** pick one of these, or tell me what's off about all five and I'll run another pass.

---

## 2. Content map

Each page: sections in order, which case sits where, the one named CTA, all laddering to
**"Inspect the repo on GitHub"** (Week 1's single action, reinforced by the persistent header CTA).

### Home
| Order | Section | Content |
|---|---|---|
| 1 | Hero | One-line claim + one supporting sentence that names the proof (grounded, observational, decision-support — not causal) |
| 2 | Featured case | Churn Prediction Model Audit teaser — the misalignment hook + the accuracy-collapse number, 2–3 sentences max |
| 3 | Proof snapshot | 2–3 bullets, each defensible in an interview, each tied directly to the proof statement — no adjacent-skill filler |
| CTA | Primary | "Inspect the repo →" (GitHub) |
| CTA | Secondary | "Read the full audit →" (internal link to Work page) |

### Work / Case Studies
| Order | Section | Content |
|---|---|---|
| 1 | Churn Prediction Model Audit (lead, full write-up) | Misaligned data/retention teams → audited accuracy collapse (reported vs. production) → precision degradation → tiered intervention recommendation. Explicit note: implementation was out of scope. |
| 2 | (second case, if ready) | *Flagged below — status unclear* |
| CTA | Per case | "View the repo →" (GitHub) — **one** CTA per case, not a stack of competing links (this is the audit already queued in memory: strip any old CTAs once the header CTA ships) |

### Method (was About)
| Order | Section | Content |
|---|---|---|
| 1 | How I audit | The process that produced the churn case: how you find the misalignment, how you measure the collapse, why you stop at recommendations instead of implementation |
| 2 | The guardrail | One paragraph on why you don't claim causation — this is a proof-statement line, not personal philosophy filler |
| CTA | Single | "See the method applied →" (internal link back to the case study — a loop, not a dead end) |

### Contact
| Order | Section | Content |
|---|---|---|
| 1 | Minimal — email address, one sentence on what kind of inquiry you want (technical leads, hiring managers) | |
| CTA | Primary | "Email me" — no GitHub duplicate here; the header CTA already covers that everywhere |

### Still need to gather (be honest — an unfinished list here blocks build week, a padded one lies to yourself)
- [ ] Real screenshot(s) of the churn audit output — the reported-vs-production accuracy comparison, specifically
- [ ] Real screenshot or chart of the precision-degradation finding
- [ ] Confirmed live GitHub repo URL with a clean README (this is the thing the whole site points at — it has to hold up)
- [ ] Exact numbers for the "accuracy collapse" (reported % vs. production %) — the site currently gestures at this; it needs real figures
- [ ] Status of a second case study — is Work page single-case for now, or is another one coming? This changes the page's section count
- [ ] Confirmed contact email for the Contact page CTA

---

## 3. Identity kit

Calm, precise, audit-grade — the mood that matches "I found where the model actually broke and
said so," not a generic SaaS-startup look. Three options each, per the assignment's own method:
you get choices, you make the call.

### Font pairing options
| Option | Heading | Body | Mood |
|---|---|---|---|
| A | Inter (Bold) | Inter (Regular) | Safe, engineering-clean, zero personality risk |
| B *(recommended)* | IBM Plex Sans | Inter | Technical without trying hard — Plex Sans reads as "built by someone who works with data," Inter keeps body text easy |
| C | Space Grotesk | Inter | Slightly more distinctive heading, still restrained |

**Recommended addition:** use **IBM Plex Mono** *only* for numbers and metric callouts (the
accuracy-collapse figures, precision numbers) — not as body text. It's a small touch that visually
marks "this is a measured number" versus prose, which reinforces the proof statement's evidence-first
framing without adding a third full typeface.

### Palette options
| Option | Text | Background | Accent | Mood |
|---|---|---|---|---|
| A *(recommended)* | `#1A1A1A` | `#FAFAFA` | `#2D5FE0` (confident blue) | Trustworthy, analytical — reads as audit, not marketing |
| B | `#111827` | `#F9FAFB` | `#0EA5E9` (sky blue) | Slightly cooler, more "product" than "audit" |
| C | `#16181D` | `#FFFFFF` | `#10B981` (emerald) | Risk: green reads as generic "growth SaaS," works against the audit/rigor positioning |

**Why A over C specifically:** your lead case study's whole story is finding where a model
*failed* honestly — green's "all systems go" association undercuts that. Blue stays neutral and
lets the actual numbers carry the emotional weight.

### Favicon / mark
Simplest option that still looks intentional: initials **"KV"** set in the heading font, accent
blue on a near-white square. No abstract logo needed — a portfolio favicon's only job is to be
recognizable in a browser tab, not to carry brand meaning.

### Style note (paste this back into any build session to stay consistent)
> Headings: IBM Plex Sans. Body: Inter. Metrics/numbers only: IBM Plex Mono. Text `#1A1A1A` on
> background `#FAFAFA`, one accent `#2D5FE0` for links and CTAs. Generous whitespace — the work is
> the color on the page, not the site.

**Before you commit:** run the WebAIM contrast checker on `#1A1A1A` on `#FAFAFA` and on
`#2D5FE0` as a link color against `#FAFAFA` — both should pass comfortably, but confirm rather
than assume.

---

## 4. Image curation

### What's actually needed (matched to the content map above)
| Page | Image | Real or generated? |
|---|---|---|
| Home | None | Neither — clean title over whitespace, per the assignment's own "reads as intentional" example. A hero image here would compete with the churn-audit teaser for attention. |
| Work — churn audit | Reported-vs-production accuracy comparison chart | **Real** — this is your actual finding, it has to be a real capture |
| Work — churn audit | Precision-degradation chart | **Real** |
| Work — churn audit | Tiered intervention table/mockup | **Real**, or a clean generated table graphic *only* if no real artifact exists — flag which |
| Method | Optional: a simple process diagram (audit steps) | Could be self-built (SVG/diagram), not AI-generated — it's structural, not decorative, so it doesn't need "one consistent generated style," it needs to be legible |
| Contact | None | — |
| Favicon | KV monogram | Self-built, not generated — a logo this simple doesn't benefit from AI generation |

**The rule this enforces:** every image on the Work page is a real capture of real output. Nothing
generated stands in for evidence — that would quietly contradict the proof statement's own
"grounded, observational" claim.

### Rejection note (modeling the exercise — you'll need to do your own once you actually generate options)
> Generated three abstract "data flow" hero images to test against the Home page. Rejected all
> three: they had the telltale AI-slop look — glassy gradient blobs, fake bokeh — and would have
> been the most colorful thing on the page, which directly violates "the design frames the work,
> it never upstages it." Went with a clean title over whitespace instead, so the real audit charts
> on the Work page stay the loudest visual thing on the site.

**Your actual task:** generate a small batch of *anything* you were considering (a hero treatment,
a section divider, whatever), reject most of them on purpose, and write one or two honest
sentences on why. That rejection note is graded on judgment, not politeness — "I liked this one"
doesn't pass; "this one has the fake-glass look and would compete with the accuracy chart" does.

---

## Self-check before you submit

- [ ] Claim is one sentence, memorable, not a paragraph
- [ ] Every page has ordered sections and exactly one named CTA, laddering to the GitHub repo
- [ ] Gather-list is honest, not padded
- [ ] One or two fonts, ~3–4 colors total, real hex codes
- [ ] Favicon/logo exists and is simple
- [ ] Style note is short enough to paste into any future build session
- [ ] Work page images are real captures, not AI stand-ins
- [ ] Rejection note shows actual reasoning, not just a preference
