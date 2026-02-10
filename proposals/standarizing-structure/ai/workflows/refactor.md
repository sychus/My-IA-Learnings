# Workflow: Refactor

> **Owner: Dev.** Rules and process for refactoring without changing behavior.

## Principle

Refactoring changes structure (names, files, patterns) without changing observable behavior. No new features, no bug fixes in the same change unless explicitly scoped.

## Before Refactoring

1. Ensure existing tests are green and sufficient; add tests for unclear behavior if needed.
2. Define scope: which modules, layers, or files are in scope.
3. Prefer small, reviewable steps over one giant refactor. Optionally track steps in `context/current-sprint.md` or a ticket.

## During Refactoring

- Follow `.ai/CONVENTIONS.md` and `.ai/ARCHITECTURE.md`.
- Preserve public APIs and contracts (see `specs/api/openapi.yaml`, `specs/domain/models.md`); if you change them, that is a separate feature or versioned change.
- Run tests after each logical step; keep the main branch green.
- Use the project's rename and move tools to keep history where possible.

## What Is In Scope

- Renaming for clarity (types, functions, files) per GLOSSARY and CONVENTIONS.
- Extracting functions, modules, or services to reduce duplication or improve structure.
- Replacing deprecated libraries with supported ones (see STACK.md).
- Improving test structure (e.g., shared fixtures, builders) without changing assertions.

## What Is Out of Scope (Do Separately)

- Changing behavior or adding features (use `new-feature.md`).
- Fixing bugs (use `bug-fix.md`).
- Changing API or domain contracts without a spec/ADR and versioning.

## After Refactoring

- Reviewer checks that behavior is unchanged and conventions are met.
- If the refactor is large, document the motivation and approach in `context/decisions-log.md` or an ADR in `docs/adr/`.
