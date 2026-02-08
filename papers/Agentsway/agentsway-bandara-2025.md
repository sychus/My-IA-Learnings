# Agentsway — Software Development Methodology for AI Agents-Based Teams (Bandara et al., 2025) — Summary

## Citation / reference

- Eranga Bandara, Ross Gore, Xueping Liang, Sachini Rajapakse, Isurunima Kularathna, Pramoda Karunarathna, et al. (2025). **“Agentsway — Software Development Methodology for AI Agents-Based Teams.”** arXiv:2510.23664v1. (Oct 2025)  
  Source (PDF in this repo): [`agentsWay.pdf`](./agentsWay.pdf)

## What problem it addresses

Traditional methodologies (Scrum, Kanban, Shape Up, XP, etc.) were designed for **human-centric teams**. As “agentic AI” starts contributing to planning, prompting, coding, testing, and learning, the paper argues we need a methodology that treats **AI agents as first-class collaborators** with governance, traceability, and privacy-by-design.

## Core idea (in one paragraph)

**Agentsway** is a development methodology where a **human orchestrator** supervises a suite of specialized AI agents (planning, prompting, coding, testing, fine-tuning). Work happens as a structured lifecycle that emphasizes governance and auditability (artifacts are version-controlled), quality gates (testing agents), and a **retrospective learning loop** where results and feedback are used to fine-tune models for future iterations—within organizational boundaries.

## Team model: roles (human + agents)

- **Human orchestrator**: interprets business goals, interfaces with stakeholders, validates artifacts, and provides governance/ethical oversight.
- **Planning agent**: turns docs/context into structured plans (tasks, dependencies, estimates, pitches) and publishes them to shared repos.
- **Prompting agent**: converts approved tasks into context-rich prompts for coding agents; prompts are logged and reviewed.
- **Coding agents**: implement code from prompts, adhering to standards/architecture; can use tools/integrations (the paper mentions MCP).
- **Testing agents**: run automated tests, static analysis, and security checks; produce structured quality reports.
- **Fine-tuning agents**: collect prompts/code/test feedback and perform retrospective fine-tuning to improve future performance (privacy-preserving).

## Lifecycle (high level)

1. **Requirements & context capture** (human-led, AI-assisted note-taking/summarization)
2. **Planning** (agent decomposes work into tasks/pitches; human approves)
3. **Prompting** (agent produces implementation prompts; human approves)
4. **Coding** (agents generate/modify code; continuous review)
5. **Testing** (agents validate correctness/security; feedback loop)
6. **LLM fine-tuning** (retrospective learning from artifacts and feedback)

## How this relates to “Scrum with agentic AI”

Instead of mapping 1:1 to classic Scrum events, the paper reframes the “team” as **human + agents** and shifts the human role towards **orchestration and governance**. A practical interpretation for Scrum teams is:

- Treat prompt specs, generated code, and test reports as **first-class sprint artifacts** (versioned, reviewable).
- Make **review & integration** explicit work (human validation, integration, quality/security gates).
- Use retrospectives not only for process tweaks, but also to decide what to **standardize / fine-tune** (prompts, policies, internal models).

## Key themes to keep in mind

- **Governance & traceability**: artifacts are published and reviewed; workflows are auditable.
- **Privacy-by-design**: learning/fine-tuning within secure/regulatory boundaries.
- **Continuous improvement**: feedback becomes training signal (when allowed).
- **Specialization**: separate agents for planning/prompting/coding/testing to reduce role overload.

## Notes / questions for follow-up

- What are the minimal “Agentsway” components that deliver value without requiring model fine-tuning?
- How do we define clear acceptance criteria and quality gates to avoid “fast chaos”?
- What metrics best capture agentic productivity + reliability in our context?

