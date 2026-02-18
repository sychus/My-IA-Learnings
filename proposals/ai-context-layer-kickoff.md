# AI-Ready Context Layer — Implementation Plan

## The Problem
Fragmented knowledge across devs and comapany repos. Adding AI agents generating code without context will multiply the problem exponentially.

## The Goal
Any new developer (human or AI) should be able to understand a repo and contribute coherent code without relying on tribal knowledge.

---

## Phase 0: Preparation (1 day)

### Define ownership
Assign a **Context Owner** per repo — the person who knows it best. They're not maintaining it alone, they're leading the initial documentation effort.

| Repo | Context Owner | Backup |
|------|--------------|--------|
| Repo 1 | __________ | __________ |
| Repo 2 | __________ | __________ |
| Repo 3 | __________ | __________ |
| Repo 4 | __________ | __________ |
| Repo 5 | __________ | __________ |

### Create the central repo
Create an `engineering-hub` repo (or whatever name you prefer) that serves as the global index. This is where the architecture map will live.

---

## Phase 1: Context Layer per Repo (Weeks 1-2)

Each Context Owner adds these files to the root of their repo:

### 1. `ARCHITECTURE.md`
```markdown
# [Repo Name]

## What it does
2-3 paragraph description of what this service/app does.

## Stack
- Main language/framework
- Database
- External services consumed
- How it's deployed (CI/CD)

## Project structure
Description of the main directories and what each one contains.
Don't list every file — explain the organizational logic.

## Patterns and conventions
- Naming conventions
- Design patterns used (e.g., service layer, repository pattern)
- How errors are handled
- How DB migrations are managed

## Dependencies with other repos
What other repos it consumes or who consumes it. Include simple diagrams if applicable.

## How to run it locally
Steps to set up the development environment from scratch.
```

### 2. `AGENTS.md` (or `.cursor/rules` if using Cursor)
```markdown
# Rules for AI Agents

## Project context
[Brief summary so the agent understands where it stands]

## Mandatory rules
- Always follow pattern [X] for new endpoints/components
- Never directly modify [critical tables/files]
- Tests go in [location] with format [format]
- Use [library X] for [thing Y], don't implement manually

## Reference examples
To create a new [endpoint/component/trigger], see as reference:
- `path/to/good/example1`
- `path/to/good/example2`

## Anti-patterns
Do NOT do this:
- [Example of code we don't want]
- [Pattern that causes problems]

## Salesforce context (if applicable)
- Relevant custom objects and their relationships
- Apex naming conventions
- Governor limits to keep in mind
```

### 3. `OWNERSHIP.md`
```markdown
# Ownership

## Areas and experts

| Area / Module | Primary expert | Contact |
|---------------|---------------|---------|
| [Module A] | [Name] | [Slack/email] |
| [Module B] | [Name] | [Slack/email] |

## Recent architecture decisions
| Date | Decision | Context | Decided by |
|------|----------|---------|------------|
| | | | |
```

---

## Phase 2: Global Map (Weeks 2-3)

In the `engineering-hub` repo, create:

### `README.md` — Architecture Map
```markdown
# Blackthorn Engineering Hub

## Our Services

[Mermaid diagram or image showing repos and their connections]

## Repo Index
| Repo | Description | Owner | Stack | Docs |
|------|------------|-------|-------|------|
| [repo1] | ... | ... | ... | [link to ARCHITECTURE.md] |

## How we work
- Link to coding standards
- Link to PR review process
- Link to deploy process

## For AI Agents
Global rules that apply across all repos:
- Security standards
- How we handle sensitive data
- Shared patterns across repos
```

---

## Phase 3: Integrate into the Workflow (Weeks 3-4)

### In the PR process
Add to PR template:
```markdown
## Checklist
- [ ] If I changed the architecture, I updated ARCHITECTURE.md
- [ ] If I added a new pattern, I updated AGENTS.md
- [ ] If I changed module ownership, I updated OWNERSHIP.md
```

### In new dev onboarding
The first task for any new developer is to read the `engineering-hub` and the `ARCHITECTURE.md` files of the repos they'll be working on.

### In agent configuration
Configure code agents (Cursor, Claude Code, etc.) to read `AGENTS.md` as base context before generating code.

---

## Success Metrics

Evaluate after one month:
- Can a new developer set up and understand a repo in less than half a day? (vs. current time)
- Do AI agents generate code that respects the repo's patterns without manual intervention?
- Has the volume of Slack questions like "who knows how X works?" decreased?

---

## Tips to Keep It Alive

1. **Start imperfect.** The first version of ARCHITECTURE.md won't be perfect. An incomplete doc is better than no doc.
2. **Do it as a team.** The Context Owner leads but the initial documentation session should be collaborative (1-2 hours per repo max).
3. **Don't duplicate.** If you already have docs elsewhere, link to them — don't copy.
4. **Quarterly review.** Schedule a review every 3 months to verify docs are still accurate.
