# Rung 1 (English): an A/B test status update

**Request:** Rewrite this status update so I can read it in one pass.

**Rung choice:** facts, a decision, next steps. No structure to draw, no parameter to drag. Rung 1.

## Before

> This week we made meaningful progress on the A/B experimentation front: overall, the new recommendation algorithm is showing a promising upward trend in CTR, our core metric (4.3% vs 4.0% control, p=0.08, not yet statistically significant), although it's worth noting that session duration has seen a slight dip (about −2%); given that the experiment currently covers only ~5% of traffic and has run for just 6 days, it would be premature to make a full rollout decision at this stage, and the team is leaning toward expanding to 20% of traffic and observing for at least another week before conducting a holistic evaluation, while in parallel investigating the root cause of the decline.

## After

> **Decision:** Do not roll out the new algorithm yet. The team is leaning toward expanding it to 20% of traffic, observing for at least one more week, then deciding.
>
> | Metric | Test | Control | Note |
> |---|---|---|---|
> | CTR | 4.3% | 4.0% | p = 0.08, not statistically significant |
> | Session duration | about −2% | — | shorter in the test group |
>
> **Why wait**
>
> - The experiment covers only about 5% of traffic.
> - The experiment has run for only 6 days.
>
> **Next**
>
> 1. Expand the experiment to 20% of traffic.
> 2. Observe for at least one more week, then decide.
> 3. Find out why session duration dropped.
>
> **What to check:** whether p = 0.08 is from a pre-registered test, and whether the −2% is relative or absolute.

## What changed

| Problem | Rule |
|---|---|
| The decision was in the last clause → moved to the first line | conclusion first |
| "meaningful progress", "promising upward trend", "holistic evaluation" → removed or made concrete | no filler |
| Two metrics buried in parentheses → a table | lists and tables for parallel facts |
| One 110-word sentence → short sentences | one idea per sentence |
| Kept "leaning toward", "about", "at least", "not statistically significant" | **nothing cut** |

The easiest word to lose is "leaning toward". Drop it, and a plan becomes a decision.
