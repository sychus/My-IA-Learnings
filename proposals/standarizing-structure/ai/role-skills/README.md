# Skills

> Project-specific skills that AI agents can use. Each **role** (Product, Dev, QA) maintains the skills in their folder. Agents read from these when working on tasks in that domain.

## Structure

| Folder | Owner | Purpose |
|--------|--------|---------|
| **product/** | Product | Skills for understanding scope, acceptance criteria, and prioritization. Agents use these when implementing or reviewing features. |
| **dev/** | Dev | Skills for architecture, patterns, tooling, and implementation. Agents use these when coding, refactoring, or reviewing. |
| **qa/** | QA | Skills for test strategy, quality gates, and bug triage. Agents use these when writing tests or following the bug-fix workflow. |

## How It Works

- **Humans** (Product, Dev, QA) add or edit `.md` files in their folder. Each file is a *skill*: instructions, examples, or rules that agents should follow when relevant.
- **Agents** (coder, reviewer, tester, etc.) are instructed to load and apply skills from the appropriate folder depending on the task (see `.ai/agents/*.md` and `.ai/OWNERSHIP.md`).
- Keep skills focused and short. Use one file per topic (e.g. `auth-acceptance.md`, `api-versioning.md`, `e2e-strategy.md`).

## Naming

- Use kebab-case: `payment-idempotency.md`, `error-messages.md`.
- Prefix by domain if useful: `product/feat-auth-criteria.md`, `qa/regression-checklist.md`.

## Example Skills

- **Product**: "How we write acceptance criteria", "Definition of done for features", "Priority levels".
- **Dev**: "How we structure API handlers", "Database migration rules", "Logging standards".
- **QA**: "When to write E2E vs integration tests", "Bug report template", "Regression scope".

See each role's folder for a placeholder and add your own.
