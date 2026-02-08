# Proposal: Standardizing Agentic Software Development

## Why standardize?

When you introduce AI agents into software delivery, consistency becomes a first-order problem:

- Different prompts produce different behaviors.
- Context drift creates subtle architectural divergence.
- “Helpful” changes can violate non-negotiable constraints (security, privacy, style, quality gates).
- Without traceability, it’s hard to audit decisions and learn from mistakes.

The goal of this proposal is to define a **repeatable, reviewable structure** that teams can adopt across projects.

## Suggested project layout

```text
project/
├── .ai-project/
│   ├── config.yml        # Configuration: which agent/model, temperatures, policies
│   ├── prompts/          # Team prompt library (reusable, versioned)
│   ├── skills/           # Custom skills/playbooks (procedures, checks, scripts)
│   ├── context/          # Project context for the AI (docs, architecture, domain)
│   ├── constraints/      # Non-negotiable rules (security, style, compliance)
│   └── audit/            # AI decision log (ADRs, rationale, trade-offs)
└── (rest of your repo)
```

## What each folder is for

- **`config.yml`**
  - Defines how the agent should operate in this repo: preferred models, determinism vs creativity, allowed tools, and escalation rules.
  - Captures environment assumptions (e.g., “do not run destructive commands”, “read-only by default”).

- **`prompts/`**
  - Your reusable building blocks: “PR description prompt”, “bug triage prompt”, “refactor prompt”, “doc update prompt”.
  - Treat prompts as code: version them, review them, keep them small and composable.

- **`skills/`**
  - Task-specific playbooks the agent must follow (e.g., “Create a new API endpoint”, “Add a database migration”, “Write a paper summary”).
  - Include checklists and quality gates (tests to run, files to update, rollback steps).

- **`context/`**
  - The minimum stable context the agent needs to stay aligned: system overview, architecture decisions, domain glossary, dependencies, runbooks.
  - Keep it curated: prefer a few “source-of-truth” docs over a pile of stale notes.

- **`constraints/`**
  - Explicit guardrails: security constraints, data handling rules, coding standards, approved libraries, compliance rules.
  - This is the place for “MUST / MUST NOT” statements.

- **`audit/`**
  - Lightweight traceability for agent-influenced decisions: ADRs, rationale for trade-offs, why a library was introduced, why a pattern was chosen.
  - Helps with accountability, onboarding, and future refactors.

## Operating model (how teams use this)

- **Before work starts**
  - Update `context/` if the system has changed.
  - Ensure `constraints/` reflect current security/compliance expectations.

- **During work**
  - Prefer prompts and skills from `.ai-project/` rather than ad-hoc prompting.
  - Any meaningful architectural choice should result in an entry under `audit/`.

- **Code review**
  - Review both code and the “agent inputs” when relevant (prompt used, skill followed, constraints satisfied).
  - Treat violations of `constraints/` as blockers, same as failing tests.

## Example `config.yml` (minimal)

```yaml
agent:
  mode: "collaborative"
  default_model: "preferred-model-name"
  temperature: 0.2

policies:
  read_only_by_default: true
  require_confirmation_for:
    - "deleting files"
    - "writing migrations"
    - "deploying"

quality_gates:
  must_run:
    - "tests"
    - "lint"

constraints:
  paths:
    - ".ai-project/constraints/"
```

## Benefits you should expect

- **More predictable outcomes** across contributors and across time.
- **Faster onboarding**: newcomers learn “how we do agentic dev here”.
- **Governance + auditability** for AI-assisted decisions.
- **Reusable leverage**: prompts/skills improve over time instead of resetting every project.

