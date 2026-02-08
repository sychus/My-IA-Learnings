# Vibe Coding in Practice: Motivations, Challenges, and a Future Outlook (Fawzy et al., 2025) — Summary

## Citation / reference

- Ahmed Fawzy, Amjed Tahir, Kelly Blincoe (2025). **“Vibe Coding in Practice: Motivations, Challenges, and a Future Outlook – a Grey Literature Review.”** arXiv:2510.00328v1 (Oct 2025).  
  PDF (in this repo): [`vibe-coding-in-practice.pdf`](./vibe-coding-in-practice.pdf)  
  arXiv: `https://arxiv.org/abs/2510.00328`

## What “vibe coding” means (as used in the paper)

**Vibe coding** is when people rely on AI code generation tools through **intuition + trial-and-error**, often **without fully understanding** the generated code.

## What the paper studies

A **systematic grey literature review** of **101 practitioner sources**, extracting **518 firsthand behavioral accounts** about:

- **RQ1**: motivations for vibe coding
- **RQ2**: user experience while vibe coding
- **RQ3**: perceptions of AI-generated code quality
- **RQ4**: quality assurance (QA) practices during vibe coding

## Key findings (high signal)

- **Speed–quality trade-off paradox**: vibe coders are motivated by **speed and accessibility**, frequently experiencing “instant success/flow”, but they also often perceive the resulting code as **fast but flawed**.
- **QA is often weak or missing**: many accounts describe skipping testing/review, trusting outputs without modification, or **delegating QA back to the AI** (creating a potentially circular “AI generated it, AI verified it” loop).
- **A new vulnerable developer profile**: especially for novices/non-software developers, vibe coding can enable shipping something they **cannot later debug or maintain**, increasing risk when issues appear.

## Practical implications (as I read it)

- Vibe coding is powerful for **rapid prototyping** and lowering barriers, but it increases the probability of:
  - **fragile software**
  - **maintainability problems**
  - a **QA gap** if organizations treat “working demo” as “production-ready”

## Recommendations highlighted in the discussion

- **For orgs/practitioners**: match tasks to skill level and provide scaffolding (guided debugging, safe templates, escalation paths) so newcomers learn to diagnose issues instead of outsourcing all QA to the AI.

## Open questions / future work (from the paper)

- How practices change as users move from non-developers → novices → professionals, and how tools should adapt safeguards to expertise.
- Whether vibe coding produces distinct defect/vulnerability patterns compared with traditional development and more structured AI-assisted workflows.
- What QA approaches actually work under vibe-coding conditions (tests, code review patterns, AI-assisted review, etc.).

