# Multi-agent workflows with Claude — Experience notes

## Context

I experimented with running **multiple agents** that collaborate to solve a single problem (instead of one assistant doing everything end-to-end).

This document captures the experience from a practitioner perspective: setup choices, what worked, what failed, and the patterns I’d reuse.

## Why try multi-agent at all?

The goal is usually one (or more) of:

- **Parallelization**: explore multiple options at once (designs, debugging hypotheses, alternatives).
- **Specialization**: assign distinct roles (planner, implementer, reviewer, tester, researcher).
- **Quality control**: introduce a deliberate “second opinion” loop (reviewer / adversary).
- **Lower cognitive load**: keep each agent prompt smaller and more focused.

## Setup (what I used)

- **Model/tools**: Claude + an environment that supports multiple cooperating agents
- **Agent roles** (example):
  - **Planner**: clarifies requirements, proposes approach, breaks work into steps
  - **Builder**: implements the change (code, config, docs)
  - **Reviewer**: critiques for correctness, risks, security, maintainability
  - **Runner/Tester**: runs checks, reproduces bugs, validates behavior

## Coordination patterns that worked

- **Shared contract**: a short, explicit “definition of done” (acceptance criteria + non-goals).
- **Single source of truth**: one place where the current plan/decisions live (e.g., a short spec or a running summary).
- **State handoff**: each agent ends with:
  - what changed / learned
  - what remains uncertain
  - recommended next action
- **Reviewer as a gate**: the reviewer approves/blocks based on explicit rules, not vibes.

## Common failure modes (what to watch for)

- **Duplicate work**: two agents implement the same thing in different ways.
- **Context fragmentation**: each agent has partial context and decisions diverge.
- **Review paralysis**: a reviewer generates endless “concerns” without prioritization.
- **Tool thrashing**: agents over-call tools instead of reasoning first.
- **Invisible decisions**: architectural trade-offs happen in chat but don’t get recorded.

## Practical guardrails

- Keep roles narrow (“Planner does not code”, “Builder does not change scope”).
- Limit parallelism when tasks require tight shared context.
- Add a lightweight decision log (see `proposals/standardizing-agentic-software-development.md`).
- Use checklists for recurring work (tests, lint, docs updates).

## What I would do differently next time

- [TODO] Reduce role overlap and clarify responsibility boundaries.
- [TODO] Add explicit quality gates earlier (tests, linters, security checks).
- [TODO] Capture decisions as short ADR-style notes as they happen.

## Notes / prompts (optional)

If you want to make this reproducible, paste:

- The role prompts for each agent
- Any shared “project context” snippet
- The acceptance criteria used
- The outcome metrics you tracked (time, rework, defects, PR iterations)

