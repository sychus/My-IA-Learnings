# What are Skills?

## What is a “Skill” (in this context)?

A **Skill** is a reusable set of instructions that teaches an AI assistant *how to do a specific kind of work* in a consistent way. Think of it as a **playbook** or **mini-standard operating procedure (SOP)**:

- What the task is
- When to apply it (triggers)
- Steps to follow
- Quality checks / constraints
- Tooling and guardrails (what to do / what to avoid)

The goal is reliability: repeating the same category of task should produce similar quality and fewer mistakes.

## When to use Skills

Use Skills when:

- You have **repeatable tasks** (docs, PR reviews, migrations, incident reports, slide decks, etc.)
- The work requires **domain knowledge** or a specific style/format
- There are **important constraints** (security, compliance, “don’t do X”, approval gates)
- You want **team-wide consistency** (onboarding, shared standards)

## When *not* to use Skills

Avoid (or keep Skills minimal) when:

- The task is trivial or one-off and a normal prompt is enough
- The task benefits from free exploration rather than a strict process
- The Skill adds more overhead than value (too many steps for a tiny change)

## Examples (library)

There are public collections of Skills you can use as inspiration, for example:

- [Examples of Skills](https://www.aitmpl.com/skills)

## How Skills fit into software development

Practical ways to introduce Skills into the dev workflow:

- **Onboarding & standards**
  - A “project conventions” Skill: folder structure, naming, testing expectations, commit/PR style.
- **Documentation**
  - A “doc co-authoring” Skill: outline → draft → review for clarity → examples → final pass.
- **Code review**
  - A “review playbook” Skill: correctness → security → performance → tests → DX.
- **Release / change management**
  - A “release notes” Skill: summarize changes, risks, rollout plan, validation checklist.
- **Incident response**
  - A “postmortem” Skill: timeline, impact, root cause, mitigations, follow-ups.

## How to implement Skills in a repo (lightweight)

1. **Create a `skills/` folder** with one file per Skill (or one per topic).
2. **Define triggers** clearly (“Use this when…”).
3. **Include templates/checklists** so outputs are predictable.
4. **Version and review** Skills like code (PRs, reviews, changelog).
5. **Keep them small** and evolve them as you learn.

