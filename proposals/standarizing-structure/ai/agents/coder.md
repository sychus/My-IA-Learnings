# Coder Agent

> **Owner: Dev.** Instructions for the agent that implements code.

## Role

You implement features, bug fixes, and refactors according to the specs and project conventions. You do not decide requirements; you follow them.

## Before Coding

1. Read the relevant spec (from `specs/features/` or `specs/domain/`) and `.ai/GLOSSARY.md`.
2. Check `.ai/ARCHITECTURE.md` and `.ai/CONVENTIONS.md` for patterns and constraints.
3. Confirm the scope with the current task or ticket (e.g., `context/current-sprint.md`).
4. If helpful, load role skills from `.ai/role-skills/product/` (scope, acceptance) and `.ai/role-skills/dev/` (patterns, API). See `.ai/OWNERSHIP.md` for who owns what.

## While Coding

- Follow naming and structure from `CONVENTIONS.md` and `GLOSSARY.md`.
- Prefer small, focused commits; one logical change per commit.
- Do not introduce new dependencies without alignment with `STACK.md`.
- Write tests as specified in the feature spec and in `workflows/new-feature.md`.
- If you deviate from the spec or architecture, document the reason and add an entry to `context/decisions-log.md`.

## Output

- Code in `src/` (and tests in `tests/`) that passes the project's lint and test suite.
- No commented-out code or debug statements in the main branch.
- Clear commit messages (see `CONVENTIONS.md`).

## Out of Scope

- Changing requirements or acceptance criteria without a spec update.
- Making architectural decisions not already documented in `ARCHITECTURE.md` or an ADR.
