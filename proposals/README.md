# Proposals

Working documents and ideas that are meant to be iterated on (not final "definitions").

## Index

| Document | Status | Description |
|----------|--------|-------------|
| [AI-First Development Guide](./AI-First%20Development-guide.md) | **Active** | Main proposal for evolving how we work — Spec-Driven Development, AI Context Layer, and a leaner workflow to replace Scrum ceremonies. |
| [AI-Ready Context Layer — Implementation Plan](./ai-context-layer-kickoff.md) | **Active** | Concrete kickoff plan for Phase 0 of the AI-First proposal (repo-level context, ownership, and structure). |
| [Standardizing structure](./standarizing-structure/) | **Deprecated** | Early exploration of team-owned prompts, skills, and global rules. Superseded by the AI-First Development Guide — keeping for reference while research continues. |

## AI-First Development Guide (start here)

The main proposal in this folder. It describes an approach to software development that takes AI coding assistants seriously as part of the workflow rather than treating them as a convenience on top of how we already work.

Key ideas:

- **Spec-Driven Development (SDD)**: written specifications drive both planning and implementation; developers spend more time authoring specs and less time writing code directly.
- **AI Context Layer (Phase 0)**: structured, shared context in each repository so AI agents generate code that respects conventions and constraints.
- **Leaner workflow**: replacing Scrum ceremonies with a process designed for AI-augmented teams.

Start here: [AI-First Development-guide.md](./AI-First%20Development-guide.md)

---

## Deprecated

### Standardizing structure

> **Status: Deprecated** — Superseded by the AI-First Development Guide. Kept for reference; needs further research before any of these ideas are revisited.

The original goal was to propose a structure that a team of humans could maintain together, where each discipline contributes prompts, skills, and rules. The ideas were folded into the broader AI-First proposal, but the specific structure (role-based skill libraries, ownership model) still needs more investigation.

Contents preserved at `standarizing-structure/` for reference.
