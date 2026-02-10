# Ownership

> This project is maintained by a **team of humans** (Product, Dev, QA). Each role owns a set of files and folders. They add or edit content in their area; AI agents then work from that information.

## Roles

| Role | Responsibility |
|------|----------------|
| **Product** | What we build: features, scope, acceptance criteria, domain language, priorities. |
| **Dev** | How we build: architecture, conventions, stack, security, API contracts, infrastructure. |
| **QA** | How we verify: test strategy, bug triage, quality gates, regression scope. |

## Who Owns What

### Product

| Asset | Purpose |
|-------|---------|
| `specs/features/` | Feature specs and acceptance criteria. Product writes or approves; uses `_template.md` for new features. |
| `specs/domain/models.md` | Domain entities and language. Product defines the "what"; Dev may advise on structure. |
| `.ai/GLOSSARY.md` | Ubiquitous language. Product owns terms; team aligns so agents use the same words. |
| `.ai/context/current-sprint.md` | Priorities and active work. Product (or Scrum Master) keeps this updated. |
| `.ai/context/known-issues.md` | Product view of known issues and debt; QA and Dev can add entries, Product prioritizes. |
| `.ai/role-skills/product/` | Product role skills: how to write/read specs, acceptance criteria, definition of done. |

### Dev

| Asset | Purpose |
|-------|---------|
| `.ai/ARCHITECTURE.md` | System design and key decisions. Dev writes; team reviews. |
| `.ai/CONVENTIONS.md` | Code style, patterns, anti-patterns. Dev owns; team follows. |
| `.ai/STACK.md` | Technologies and versions. Dev owns; changes go through decisions-log or ADR. |
| `.ai/SECURITY.md` | Security policies and boundaries. Dev owns with security review. |
| `specs/api/openapi.yaml` | API contracts. Dev maintains; Product may request endpoints. |
| `.ai/workflows/` | New-feature, bug-fix, refactor, deploy. Dev defines; QA/Product consume. |
| `.ai/agents/` | Instructions for coder, reviewer, tester, security, stylist. Dev owns; QA may co-own tester.md. |
| `.ai/context/decisions-log.md` | Technical decisions. Dev appends; anyone can request an entry. |
| `infrastructure/` | IaC (Terraform, Docker). Dev owns. |
| `.ai/role-skills/dev/` | Dev role skills: API patterns, structure, tooling, migrations. |

### QA

| Asset | Purpose |
|-------|---------|
| `.ai/agents/tester.md` | Instructions for the QA/tester agent. QA owns; Dev may align with tooling. |
| `.ai/workflows/bug-fix.md` | Bug-fix protocol. QA drives process; Dev implements fixes. |
| `.ai/context/known-issues.md` | QA adds test/quality issues; Product prioritizes. |
| `tests/` | Test layout and strategy. QA defines structure and coverage expectations; Dev/agents implement. |
| `.ai/role-skills/qa/` | QA role skills: test levels, regression checklist, bug report format. |

## How Agents Use This

- **Coder**: Reads Product specs (features, domain, glossary), Dev docs (architecture, conventions, stack, API), and role skills from `role-skills/dev/` and `role-skills/product/` as needed.
- **Reviewer**: Uses same docs plus `agents/reviewer.md`; can use skills from any role when relevant.
- **Tester**: Reads specs and `agents/tester.md`, plus `role-skills/qa/` and `role-skills/product/` for acceptance and test strategy.
- **Security**: Reads `SECURITY.md`, architecture, and code; uses `skills/dev/` if relevant.
- **Stylist**: Reads conventions and UI-related specs; can use `skills/dev/` for front-end patterns.

When in doubt, agents should prefer the **owner’s** version of a file (Product for scope, Dev for how to build, QA for how to test) and ask humans when ownership is unclear.
