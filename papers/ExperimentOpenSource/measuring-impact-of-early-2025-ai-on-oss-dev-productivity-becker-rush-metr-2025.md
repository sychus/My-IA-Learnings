# Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity (Becker & Rush et al., 2025) — Summary

## Citation / reference

- Joel Becker, Nate Rush, Beth Barnes, David Rein (METR) (2025). **“Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity.”** arXiv:2507.09089v2 (Jul 2025).  
  PDF (in this repo): [`IA impact in openSource project.pdf`](./IA%20impact%20in%20openSource%20project.pdf)  
  arXiv: `https://arxiv.org/abs/2507.09089`

## Research question

In real, mature open-source projects where developers have deep prior context, do frontier AI tools (Feb–Jun 2025) **speed up** experienced contributors—or not?

## Method (high level)

Randomized controlled trial (RCT):

- **16 experienced OSS developers** (moderate AI experience)
- **246 real tasks/issues** in mature repos developers regularly contribute to (≈ **5 years prior repo experience** on average)
- Each task randomized to **AI allowed** vs **AI disallowed**
- When AI was allowed, developers mainly used **Cursor Pro** with **Claude 3.5 / 3.7 Sonnet**
- Collected **screen recordings** and additional qualitative/quantitative data to analyze mechanisms

Primary outcome: **time to complete tasks** (tasks defined before random assignment, aiming for a fixed outcome measure).

## Main result

Despite strong expectations of speedup:

- Developers forecast **~24% faster** with AI (pre-task).
- After the study, developers estimated **~20% faster** with AI.
- The measured effect was the opposite: **AI allowed increased completion time by ~19%** (i.e., developers were slower with AI tools in this setting).

The paper also reports that external experts (economics + ML) substantially overestimated expected speedup.

## What might explain the slowdown (mechanisms + factor analysis)

The authors analyze **21 hypothesized factors** that could contribute to slowdown and group them into:

- **Direct productivity loss** (AI use actively adds overhead)
- **Experimental artifacts** (design/setup confounders)
- **Factors raising human performance** (deep context, repo quality bars, etc.)
- **Factors limiting AI performance** (tool/model limits in high-context codebases)

From labeled screen recordings and other data, a key behavioral pattern is that when AI is allowed, developers spend **less time actively coding/searching** and more time **prompting**, **waiting**, and **reviewing AI outputs**—which can dominate any gains from faster code generation.

The paper evaluates specific hypotheses (e.g., scope creep, ordering effects, learning effects with Cursor experience) and reports mixed evidence across them, while emphasizing that the overall slowdown appears robust across many analyses even if experimental artifacts can’t be fully ruled out.

## Practical takeaways

- Frontier AI tools can be **net-negative for speed** in high-context, high-quality-bar OSS work—especially when the work requires nuanced repo knowledge and careful review.
- Expectations (even from experienced developers and experts) may be **miscalibrated**, so organizations should measure impact in their own environment instead of relying on intuition.
- Tooling that reduces **prompt/review/wait overhead** (better workflows, scaffolding, or domain adaptation) may be necessary to realize speedups in mature codebases.

