# Workflow: New Feature

> **Owner: Dev.** Step-by-step process for implementing a new feature. Agents and humans follow this.

## 1. Spec Exists

- A feature spec exists in `specs/features/` (e.g., `feat-XXX-name.md`).
- Spec includes: summary, acceptance criteria, out-of-scope, and references to domain/API if needed.
- If not: human creates spec (from `_template.md`) before implementation.

## 2. Plan

- Coder reads spec and `.ai/ARCHITECTURE.md`, `.ai/CONVENTIONS.md`, `.ai/GLOSSARY.md`.
- Identify touched areas: `src/`, API (`specs/api/`), domain (`specs/domain/`).
- If API or domain changes: update `specs/api/openapi.yaml` or `specs/domain/models.md` and get agreement.
- Optionally: break into smaller tasks and note in `context/current-sprint.md`.

## 3. Implement

- Coder implements in `src/` following CONVENTIONS and STACK.
- One logical change per commit; clear commit messages.
- No new dependencies without STACK alignment; document in decisions-log if needed.

## 4. Tests

- Tester (or coder following tester instructions) adds/updates tests per spec:
  - Unit tests for new logic.
  - Integration tests for new or changed API/DB behavior.
  - E2E only for critical user paths if defined in spec.
- All tests must pass; no flake.

## 5. Review

- Reviewer agent (or human) runs the review checklist from `.ai/agents/reviewer.md`.
- Security-sensitive features get a pass from security agent (`.ai/agents/security.md`).
- UI changes get a pass from stylist (`.ai/agents/stylist.md`) if applicable.
- Address all blocking comments before merge.

## 6. Merge and Deploy

- Merge to the main branch (or release branch) per team policy.
- Deployment follows `.ai/workflows/deploy.md`.
- If the feature is user-facing, update `context/current-sprint.md` or release notes as needed.

## 7. Documentation

- Update `docs/` or ADRs if the feature introduces architectural or contract changes.
- Add an entry to `context/decisions-log.md` for any significant deviation from spec or architecture.
