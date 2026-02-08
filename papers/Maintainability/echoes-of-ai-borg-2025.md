# Echoes of AI: Investigating the Downstream Effects of AI Assistants on Software Maintainability (Borg et al., 2025) — Summary

## Citation / reference

- Markus Borg, Dave Hewett, Nadim Hagatulah, Noric Couderc, Emma Söderberg, Donald Graham, Uttam Kini, Dave Farley (2025). **“Echoes of AI: Investigating the Downstream Effects of AI Assistants on Software Maintainability.”** arXiv:2507.00788v2 (Dec 2025).  
  PDF (in this repo): [`Echoes of AI_ Investigating the Downstream Effects of AI Assistants on Software Maintainability.pdf`](./Echoes%20of%20AI_%20Investigating%20the%20Downstream%20Effects%20of%20AI%20Assistants%20on%20Software%20Maintainability.pdf)  
  arXiv: `https://arxiv.org/abs/2507.00788`

## What question the paper asks

AI coding assistants often improve **developer productivity**, but do they change **maintainability**—i.e., how easily *other developers* can later understand and evolve the resulting code?

## Method (high level)

A preregistered, two-phase controlled experiment with **151 participants** (≈95% professional developers):

- **Phase 1 (creation)**: participants added a feature to a Java web app **with or without** AI assistance.
- **Phase 2 (downstream evolution / RCT)**: new participants evolved those Phase 1 solutions **without AI assistance**.

Maintainability was primarily measured as the ease of evolution by a different developer, using metrics such as **completion time** and **code quality** (including CodeScene CodeHealth and test coverage as additional lenses).

## Key findings

- **Downstream maintainability impact (Phase 2)**: no statistically meaningful differences were found in subsequent evolution **time** or **code quality** between code originally developed with AI assistance vs without.
- **Size of any downstream effect**: Bayesian analysis suggests any speed/quality improvements were **at most small and highly uncertain**.
- **Productivity effects (Phase 1)**: AI assistance correlated with faster completion:
  - ~**30.7% median reduction** in completion time overall
  - habitual AI users showed an estimated **~55.9% speedup**

## Practical takeaways

- In the scope of this experiment and measures, the paper reports **no consistent warning signs** that AI-assisted coding degrades code-level maintainability for subsequent human evolution.
- Productivity gains do not automatically imply maintainability gains; treat them as **separate outcomes** to monitor.

## Risks and future work highlighted

The paper calls out areas that may still matter in real-world settings and deserve further study:

- **Code bloat** from excessive generation
- **Cognitive debt** if developers offload too much understanding to assistants
- The rising shift from assistants to more autonomous **coding agents**, which may change downstream effects

