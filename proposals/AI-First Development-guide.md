# AI-First Development
### A Proposal for Evolving How We Work

---

## What This Is

This document is a proposal. It describes an approach to software development that I believe is worth trying — one that takes AI coding assistants seriously as part of the workflow rather than treating them as a convenience on top of how we already work.

I'm not claiming this is the definitive answer. The practices described here are emerging, the tooling is evolving fast, and anyone who tells you they have it fully figured out is overstating it. What I believe is that the current moment is a good time to experiment deliberately, learn together, and build shared practices before our individual habits diverge too much.

I feel we need to replace our Scrum ceremonies with a leaner workflow centered on **Spec-Driven Development (SDD)** — a methodology where written specifications drive both planning and implementation, and AI handles a larger share of the coding work. The expected shift is that developers spend more time authoring and refining specifications, and less time writing code directly.

This proposal is organized in the order I think it makes sense to approach it.

---

## Why Now

Our current Scrum process was designed for teams where humans write all the code. AI coding assistants change some of the underlying assumptions: planning and specification become higher-leverage activities, and the bottleneck shifts from "writing code" toward "clearly expressing what needs to be built."

I think there is an opportunity to redesign our workflow around that shift rather than layer AI tools on top of a process that wasn't built for them. This proposal is my attempt at that redesign.

I also think there is a risk in not acting: if each developer adopts their own informal AI workflow, we end up with fragmented practices, inconsistent output quality, and codebases that become harder to navigate over time — both for humans and for AI agents.

---

## Phase 0: AI Context Layer

> I'd suggest treating this as a prerequisite before adopting the SDD workflow below. Without shared, structured context in each repository, AI agents will generate code that works in isolation but ignores the conventions and constraints that make our codebases coherent.

### The Problem This Addresses

Knowledge about our codebases is fragmented across developers and repositories. This is a pre-existing problem, but introducing AI agents without addressing it would amplify it — agents generating code without context will compound inconsistency rather than reduce it.

The goal is straightforward: any new contributor — human or AI — should be able to understand a repository and produce coherent code without relying on tribal knowledge.

📄 Full proposal: [`ai-context-layer-kickoff.md`](https://github.com/sychus/My-IA-Learnings/blob/main/proposals/ai-context-layer-kickoff.md)

---

### Step 0.1 — Preparation (Day 1)

**Assign a Context Owner per repository.** This is the person who knows the repo best. They are not responsible for maintaining documentation alone — they lead the initial effort and coordinate with the team.

| Repo | Context Owner | Backup |
|------|--------------|--------|
| Repo 1 | | |
| Repo 2 | | |
| Repo 3 | | |
| Repo 4 | | |
| Repo 5 | | |

**Create an `engineering-hub` repository.** A central repo that serves as the global index: architecture map, repository index, cross-repo standards, and global AI agent rules.

---

### Step 0.2 — Context Layer per Repository (Weeks 1–2)

Each Context Owner adds three files to the root of their repository. The templates below are starting points — I expect teams to adapt them to what actually makes sense for their codebase.

#### `ARCHITECTURE.md`

```markdown
# [Repo Name]

## What it does
2–3 paragraph description of what this service or application does.

## Stack
- Main language / framework
- Database
- External services consumed
- Deployment and CI/CD

## Project structure
Description of the main directories and the organizational logic behind them.
Do not list every file — explain the structure.

## Patterns and conventions
- Naming conventions
- Design patterns in use (e.g., service layer, repository pattern)
- Error handling approach
- Database migration strategy

## Dependencies with other repositories
Which repos this service consumes and which repos consume it.

## How to run locally
Steps to set up the development environment from scratch.
```

#### `AGENTS.md` (or `.cursor/rules` if using Cursor)

```markdown
# Rules for AI Agents

## Project context
[Brief summary so the agent understands the codebase and its purpose]

## Mandatory rules
- Always follow pattern [X] for new endpoints / components
- Never directly modify [critical tables or files]
- Tests go in [location] with format [format]
- Use [library X] for [purpose Y] — do not implement manually

## Reference examples
To create a new [endpoint / component / trigger], use these as reference:
- `path/to/good/example1`
- `path/to/good/example2`

## Anti-patterns
- [Pattern that causes problems]
- [Code style we explicitly avoid]

## Salesforce context (if applicable)
- Relevant custom objects and relationships
- Apex naming conventions
- Governor limits to keep in mind
```

#### `OWNERSHIP.md`

```markdown
# Ownership

## Areas and experts

| Area / Module | Primary Expert | Contact |
|---------------|---------------|---------|
| [Module A] | [Name] | [Slack] |

## Recent architecture decisions

| Date | Decision | Context | Decided by |
|------|----------|---------|------------|
| | | | |
```

---

### Step 0.3 — Global Architecture Map (Weeks 2–3)

In the `engineering-hub` repository, create a `README.md` with:

```markdown
# Engineering Hub

## Services Overview
[Diagram showing repositories and their connections]

## Repository Index
| Repo | Description | Owner | Stack | Docs |
|------|------------|-------|-------|------|
| repo-name | ... | ... | ... | [ARCHITECTURE.md] |

## How We Work
- Link to coding standards
- Link to PR review process
- Link to deployment process

## Global Rules for AI Agents
Standards that apply across all repositories:
- Security requirements
- How we handle sensitive data
- Shared patterns and conventions
```

---

### Step 0.4 — Integrate into the Workflow (Weeks 3–4)

**PR template.** A lightweight checklist to keep the context layer current:

```markdown
## Context Layer Checklist
- [ ] If I changed the architecture, I updated ARCHITECTURE.md
- [ ] If I added a new pattern or convention, I updated AGENTS.md
- [ ] If module ownership changed, I updated OWNERSHIP.md
```

**New developer onboarding.** The first task for any new developer would be to read the `engineering-hub` and the `ARCHITECTURE.md` of the repositories they will work on.

**Agent configuration.** AI coding tools (Claude Code, Cursor, etc.) should be configured to read `AGENTS.md` as base context before generating code.

---

### How I'd Know If This Is Working

After one month, I'd ask:

- Can a new developer understand and set up a repository in under half a day?
- Do AI agents generate code that respects existing patterns without manual correction?
- Has the volume of "who knows how X works?" questions in Slack decreased?

---

### A Few Practical Notes

- **Start imperfect.** An incomplete `ARCHITECTURE.md` is better than no documentation. I'm not aiming for exhaustive docs — just enough context to be useful.
- **Document as a team.** The Context Owner leads but the initial session should be collaborative — 1–2 hours per repository is a reasonable target.
- **Do not duplicate.** If documentation already exists elsewhere, link to it rather than copying it.
- **Revisit quarterly.** Schedule a brief review every three months to verify that context files are still accurate.

---

## Understanding Spec-Driven Development

> Reference: [Birgitta Böckeler — "Understanding SDD: Kiro, spec-kit, and Tessl"](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) (Thoughtworks, 2025)

Spec-Driven Development is an approach where a written specification is created before any code is written. The spec serves as the shared source of truth between the developer and the AI throughout the lifecycle of a feature — rather than the code itself being the primary artifact.

This is still an emerging practice. The tooling is immature, the definitions are still in flux, and the research on long-term effectiveness in production codebases is limited. That said, the core idea is sound and aligns well with what I'm observing in practice: the quality of AI-assisted implementation is largely determined by the quality of the input it receives.

### Three Levels of Adoption

I'm not proposing to adopt all levels immediately. The table below describes the spectrum so we can have a shared vocabulary.

| Level | Description | My Stance |
|-------|-------------|------------|
| **Spec-first** | Write a spec before implementation; it may be discarded after | Minimum viable starting point |
| **Spec-anchored** | Keep the spec in the repo and evolve it alongside the code | Where I'd like to land |
| **Spec-as-source** | Humans edit only specs; AI generates all code | Not a near-term goal |

### Memory Bank vs. Spec

Two distinct concepts that are easy to conflate:

| Memory Bank | Spec |
|-------------|------|
| Always active; applies to the entire codebase | Scoped to a specific feature or change |
| `AGENTS.md`, `ARCHITECTURE.md`, etc. | `specs/feature-name/requirements.md`, etc. |
| Describes how we work and how the system is built | Describes what we are building right now |
| Maintained indefinitely | Evolves with the feature |

### Suggested Spec File Structure

```
specs/
  payments-v2/
    requirements.md    ← user stories + acceptance criteria
    plan.md            ← implementation approach + todo list
  onboarding-redesign/
    requirements.md
    plan.md
```

---

## A Proposed Daily Workflow

> Reference: [Boris Tane — "How I Use Claude Code"](https://boristane.com/blog/how-i-use-claude-code/) (2026)

The workflow below is one developer's well-documented practice after nine months of working with Claude Code daily. I'm not proposing to adopt it wholesale without adaptation — but it offers a concrete starting point to iterate on.

The central principle, which I do think is worth anchoring to:

> **Do not allow the AI to write code until you have reviewed and approved a written plan.**

This single discipline — separating planning from execution — appears to be the highest-leverage practice in AI-assisted development. It prevents wasted implementation effort, keeps architectural decisions with the developer, and produces consistently better results than prompting directly to code.

---

### Step 1 — Research

Before planning any non-trivial task, ask the AI to thoroughly read the relevant parts of the codebase and produce a written `research.md` file.

**Example prompts:**
```
Read this folder in depth. Understand how it works, what it does,
and all its specificities. When done, write a detailed report of
your findings in research.md.
```
```
Study the notification system in great detail. Understand its
intricacies and write a detailed research.md with everything
there is to know about how notifications work in this codebase.
```

Use explicit language: *"in depth"*, *"in great detail"*, *"all its specificities"*. Without these signals, the AI will do a surface-level read and move on.

The resulting `research.md` is your review surface before planning begins. If the AI misunderstood a system, correct it before moving forward. The most common failure mode in AI-assisted development is not bad syntax — it is implementations that work in isolation but break surrounding systems. This phase is specifically designed to catch that.

---

### Step 2 — Planning

After reviewing the research, ask for a detailed `plan.md`.

**Example prompts:**
```
I want to build <feature name and description>. Write a detailed plan.md
for how to implement this. Include code snippets. Read source files before
suggesting changes — base the plan on the actual codebase.
```

A useful plan includes the chosen approach and rationale, code snippets showing key changes, file paths to be modified, and relevant trade-offs.

If a comparable feature exists in another codebase or open source project, share the relevant code alongside the request. The AI produces significantly better plans with a concrete reference to work from.

---

### Step 3 — Annotation Cycle

After the AI writes `plan.md`, open it in your editor and add inline notes directly into the document where something is wrong, incomplete, or needs to be redirected. Then ask the AI to address all notes and update the plan — without implementing yet.

```
Claude writes plan.md
  → You review it and add inline notes
    → You ask Claude to address all notes and update the plan
      → Repeat until the plan accurately reflects your intent
        → Request a todo list, then proceed to implementation
```

**Examples of inline annotations:**
- `"use drizzle:generate for migrations, not raw SQL"` — domain knowledge the AI doesn't have
- `"this should be a PATCH, not a PUT"` — correcting a wrong assumption
- `"remove this section — we don't need caching here"` — rejecting a proposed approach

After adding notes:
```
I added notes to the document. Address all of them and update the plan
accordingly. Do not implement yet.
```

The *"do not implement yet"* instruction is required every time. Without it, the AI will begin coding as soon as it considers the plan ready.

This cycle typically runs 1 to 6 times. When the plan is right, add the task breakdown:

```
Add a detailed todo list to the plan, with all phases and individual
tasks required to complete the implementation. Do not implement yet.
```

---

### Step 4 — Implementation

When the plan is approved:

```
Implement everything in the plan. When you finish a task or phase, mark it
as completed in the plan document. Do not stop until all tasks and phases
are done. Do not add unnecessary comments or jsdocs. Do not use `any` or
`unknown` types. Continuously run typecheck to catch issues early.
```

Your role now shifts from architect to supervisor. Corrections should be short and specific. When an implementation goes in the wrong direction, revert rather than patch:

```
I reverted everything. The only goal now is [narrow, specific scope]. Nothing else.
```

---

### Step 5 — Verification

Before considering a feature complete, verify the implementation against the specification. This is a separate activity from implementation — the goal is not to review code style, but to confirm that the system behavior matches the requirements and acceptance criteria defined in `requirements.md`.

This step exists because AI-assisted implementations can satisfy the literal tasks in a todo list while missing the original intent. Explicit verification closes that gap.

Verification can include running automated tests, manual validation against acceptance criteria, and asking the AI to compare what was built against what was specified:

```
Review the implementation and compare it against requirements.md.
List any discrepancies, missing behaviors, or inconsistencies.
Do not suggest improvements beyond the scope of the spec.
```

A feature is considered complete when:

- All items in `plan.md` todo list are checked off
- All automated tests pass
- All acceptance criteria in `requirements.md` are satisfied
- No unresolved discrepancies remain between spec and implementation
- Relevant context layer files (`ARCHITECTURE.md`, `AGENTS.md`) have been updated if needed

---

## How This Would Map to Our Current Ceremonies

I'm not proposing to eliminate all structure — I'm proposing to replace the current structure with something lighter and more aligned with how AI-assisted work actually flows.

| Current (Scrum) | Proposed |
|-----------------|----------|
| Sprint Planning | **Spec Review** — team reads and approves `requirements.md` and `plan.md` before work begins |
| Daily Standup | Async Slack update: current task, plan status, blockers |
| Backlog Refinement | Annotation Cycle — developer and AI co-author and refine the spec |
| Sprint Review | **Demo** — working software reviewed against the accepted spec |
| Sprint Retrospective | Short retro with a fixed question: *"What should we update in our context layer files?"* |
| User Story | `specs/[feature]/requirements.md` |
| Definition of Done | All todo items checked, tests passing, implementation verified against `requirements.md` |

---

## Spec Templates

### `specs/[feature-name]/requirements.md`

```markdown
Status: Draft | Approved | In Progress | Verified | Released
Owner: [Name]
Created: [Date]
Last Updated: [Date]

# [Feature Name] — Requirements

## Context
[Why this feature is needed]

## User Stories
- As a [role], I want [capability] so that [outcome]

## Acceptance Criteria
- GIVEN [precondition] WHEN [action] THEN [expected result]

## Out of Scope
[Explicitly list what this spec does not cover]
```

### `specs/[feature-name]/plan.md`

```markdown
# [Feature Name] — Implementation Plan

## Approach
[Overall strategy and rationale]

## Files to Modify
- `path/to/file.ts` — [description of changes]

## Key Implementation Details
[Code snippets for non-obvious parts]

## Trade-offs
[What we are accepting and why]

## Todo List
- [ ] Phase 1: [name]
  - [ ] Task 1.1 — [description]
  - [ ] Task 1.2 — [description]
- [ ] Phase 2: [name]
  - [ ] Task 2.1 — [description]
```

---

## Let's Try It First

Before committing to anything, I'd rather pick one small feature, run it through this entire workflow, and see what actually happens. Not a formal pilot with success metrics and a review committee — just one real task, done this way, with honest notes afterward about what helped and what got in the way.

If it creates more friction than it removes, we adjust or drop it. If it works, we have something concrete to build on. The goal is to fail fast and cheap before deciding anything.

---

## A Final Thought

We are at a genuinely strange moment in software development. The tools are changing faster than our processes, and most teams — including us — are improvising. This proposal is my attempt to be a little more intentional about that improvisation.

I don't know if this will work exactly as described. Some of it probably will, some of it probably won't, and there are almost certainly things we'll need to figure out that none of the references I cited have encountered yet.

---

## References

- Böckeler, B. (2025). [Understanding Spec-Driven Development: Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html). Thoughtworks / Martin Fowler's blog.
- [Spec-Driven Development: A Practical Guide](https://docs.zencoder.ai/user-guides/tutorials/spec-driven-development-guide). Zencoder documentation.
- Tane, B. (2026). [How I Use Claude Code](https://boristane.com/blog/how-i-use-claude-code/).
- [AI Context Layer Kickoff](https://github.com/sychus/My-IA-Learnings/blob/main/proposals/ai-context-layer-kickoff.md). Internal proposal.