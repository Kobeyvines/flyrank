# Portfolio Case Studies

## Voice Card (standing instruction)
**Direct, warm, professional, accessible, sharp.**
- Direct: say the point in the first sentence, don't build up to it.
- Warm: sound like a person, not a corporate brochure.
- Professional: no slang, no forced casualness.
- Accessible: a non-technical stakeholder should understand the problem and outcome without needing jargon explained.
- Sharp: no filler, no "results-driven," no hedging. Every sentence earns its place.

---

## Case Study: Customer Churn Model Audit

### The Problem
A company's data team and customer retention team were blaming each other. Retention was spending real money — airtime, cashback, discounts — to keep customers from leaving, but customers kept leaving anyway. Retention said the model was faulty. Data said the model was fine and the problem was implementation. Nobody could say who was right, so the money kept burning while the argument continued. I was brought in to audit the model and settle it.

### What I Did
I pulled the model out of the boardroom argument and put it in front of production data. The consultancy had reported 87% accuracy. In production, it was running at 55% — barely better than a coin flip.

Here's why nobody caught it: 73% of the company's customers were loyal. A model that predicted "nobody churns" would already be 73% accurate while catching zero real churners. Accuracy was hiding the real story, so I looked at precision instead — and it had collapsed from 0.82 to 0.36. Two out of every three customers flagged as "about to churn" weren't going to churn at all. The team was handing out incentives to loyal customers who didn't need them, while missing the churners who actually mattered.

I traced the cause to a threshold set for safety over sustainability — it was tuned to catch 86% of churners, and that aggressiveness is what wrecked precision. Digging into the behavior data, I found the model treated a 14-day quiet period as a churn signal, when actual churners averaged 24 days of silence. It was flagging normal customer behavior as a red flag. I also found the model was missing high-value churners entirely — users with 15 monthly transactions and healthy balances who left anyway, because the model had no way to notice a *decline* from someone's own normal, only a flat low-activity threshold.

My recommendation: replace the blanket "catch everyone" approach with a tiered strategy — high-risk customers get immediate outreach, medium-risk get low-cost automated nudges, low-risk get monitored, not spent on. I also proposed new features built around each customer's own behavior pattern rather than fixed cutoffs, and an A/B test comparing human check-ins against financial incentives, since the flat-incentive approach was converting at only 9%.

### What Came of It
I handed off the audit and the action plan. Implementation wasn't part of my scope, and I want to be honest about that rather than imply a result I didn't measure — I'd have welcomed staying on through rollout to see the tiered strategy tested against real outcomes. What I can stand behind is the diagnosis: I found exactly why a "good" model was failing in the real world, and gave the team a specific, arguable reason to stop pointing fingers and start fixing the right thing.

**See the audit and the code:** [github.com/Kobeyvines/CASE_STUDY](https://github.com/Kobeyvines/CASE_STUDY)

---

## Bio
I take machine learning models out of notebooks and put them where the money actually gets spent or saved. My work doesn't stop at "the model scored well" — it asks whether the model is actually doing what a business needs, and says plainly when it isn't.

## Contact / CTA
Have data piling up and no one to turn it into a decision you can trust? Email me — I'll walk you through exactly how I found a hidden 32-point accuracy gap in a churn model and what I'd have done next.

---

## Before / After: One Line, Two Ways

**Generic AI version:**
> "Leveraged advanced machine learning techniques to drive significant improvements in customer retention outcomes and deliver actionable business insights."

**Edited, in-voice version:**
> "The model was reported at 87% accuracy. In production, it was 55% — I found out why, and told the team exactly what to fix before they spent another shilling on the wrong customers."

The generic version could describe any project by any person. The edited version names a real number, a real gap, and a real decision — it can only be this project.
