# Agile in the Age of AI (Yuji Isobe, 2025) — Summary

## Reference

- Yuji Isobe (Jun 22, 2025). **“Agile in the Age of AI: A Practitioner’s Guide to Evolving Scrum”**. Medium.  
  Link: `https://medium.com/@yujiisobe/agile-in-the-age-of-ai-a-practitioners-guide-to-evolving-scrum-a94966326571`

## Brief summary

The article argues that generative AI does **not replace Agile**, it amplifies it: by accelerating the creation of software (code, tests, documentation), it **shortens feedback loops** dramatically. But “doing the same things faster” can create chaos, so Scrum practices need to evolve to become more “AI-native”.

Core ideas:

- **From fixed sprints to hybrid workflows**: for exploratory/experimental work (common in AI), **Kanban / continuous flow** fits better; for well-defined engineering work, **sprints** can still be effective. The recommendation is a **hybrid model** that matches the process to the type of work.
- **Beyond velocity**: with AI, velocity becomes an even worse proxy. The suggestion is to measure value flow with metrics such as:
  - **Cycle time** (from when work starts to when it’s completed)
  - **Lead time** (from when an idea is conceived to when it delivers value in production)
  For experimental AI work, the “deliverable” can be **validated learning** (including proving a hypothesis is wrong).
- **AI as a “teammate”**: reframes AI as a “cybernetic teammate” that **augments** roles (PO, SM, dev). The developer shifts from typing code to **architecting, guiding (prompting), and critically reviewing**.
- **A new estimation approach**: traditional story points break down when code generation approaches “near-zero effort”. It suggests a 3-type framework:
  - **Zero-point**: truly end-to-end automated tasks with no manual review.
  - **Review & Integration (R&I)**: a category to estimate the human work of **prompting, validating, integrating, refactoring, and reworking** AI output.
  - **Standard**: mostly human-led work (creativity/strategy/complex architecture).
- **An incremental playbook**: start with high-value, low-risk automation; treat prompting as a discipline (structured prompts, shared prompt library); and reinforce **human-in-the-loop** for quality/security (including guardrails for sensitive data).

## Why this is useful (practical takeaways)

- If your team uses coding assistants, **R&I stories** help you acknowledge (and plan for) the review/integration work that does not “go away”.
- Shifting focus from “velocity” to **cycle/lead time** tends to reflect real improvement more accurately when introducing AI.
- For high-uncertainty features, it’s worth formalizing **learning goals** in reviews (not only demos).

## For more info

See the original Medium article: `https://medium.com/@yujiisobe/agile-in-the-age-of-ai-a-practitioners-guide-to-evolving-scrum-a94966326571`

