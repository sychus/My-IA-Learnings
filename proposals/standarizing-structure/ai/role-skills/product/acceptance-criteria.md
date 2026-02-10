# Acceptance criteria (Product skill)

> **Owner: Product.** How we write and interpret acceptance criteria so agents implement the right thing.

- Each criterion must be **testable** (can be verified by code or manual check).
- Use **user/domain language** from `GLOSSARY.md`; avoid implementation jargon.
- Prefer "User can…" or "System must…" for clarity.
- If a criterion depends on another feature, say so explicitly.
- Edge cases (errors, empty state, timeouts) should have at least one criterion when they matter for the feature.

Agents (coder, tester, reviewer) should treat acceptance criteria as the source of truth for "done" and report back if any criterion is ambiguous or conflicting.
