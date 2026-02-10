# Workflow: Bug Fix

> **Owner: QA** (process); **Dev** (implementation). Protocol for identifying, fixing, and verifying bugs.

## 1. Reproduce and Specify

- Describe the bug: expected vs actual behavior, steps to reproduce, environment.
- If not already in `context/known-issues.md`, add a short entry (title, severity, link to issue/ticket).
- Define "done": what behavior must hold after the fix (acceptance criteria).

## 2. Root Cause

- Coder (or debugger) finds root cause; avoid fixing symptoms only.
- If the bug indicates a spec or design flaw, note it and consider a spec update or ADR.
- Document non-obvious findings in the ticket or in `context/decisions-log.md`.

## 3. Fix

- Coder implements the fix in `src/` following CONVENTIONS.
- Change set is minimal: only what is needed to fix the bug.
- No unrelated refactors unless agreed and tracked separately.

## 4. Test

- Add or extend a test that would have caught this bug (regression test).
- Ensure existing tests still pass.
- If the bug is security-related, security agent reviews (`.ai/agents/security.md`).

## 5. Review

- Reviewer runs the checklist from `.ai/agents/reviewer.md`.
- Fix is verified in the described environment (or CI) before merge.

## 6. Merge and Deploy

- Merge per team policy; deploy per `.ai/workflows/deploy.md`.
- If the bug was user-facing or security-related, consider communication or release note.

## 7. Close and Learn

- Close the ticket and, if applicable, the entry in `context/known-issues.md`.
- Optionally: short blameless post-mortem or decision-log entry if the bug revealed process or design gaps.
