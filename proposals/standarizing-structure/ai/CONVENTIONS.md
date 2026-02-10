# Conventions

> **Owner: Dev.** Human-written. Code style, patterns, and anti-patterns for the project.

## Code Style

- **Language / framework**: (e.g., TypeScript, Python 3.11+)
- **Formatting**: (e.g., Prettier, Black) — config file location
- **Linting**: (e.g., ESLint, Ruff) — config and rule set
- **Naming**: (e.g., camelCase for functions, PascalCase for types, kebab-case for files)

## Patterns to Follow

- **Error handling**: (e.g., use Result types, never swallow exceptions)
- **Logging**: (e.g., structured JSON logs, log levels)
- **Configuration**: (e.g., env vars, no secrets in code)
- **Dependencies**: (e.g., minimal dependencies, pin versions)

## Anti-Patterns to Avoid

- No business logic in controllers; use services/use cases.
- No raw SQL without parameterization.
- No hardcoded URLs or credentials.
- No silent `catch` without logging or rethrow.

## File and Folder Structure

- Where to put new modules, shared code, and tests.
- Naming for components, hooks, and utilities.

## Git

- Branch naming: `feature/`, `fix/`, `chore/`
- Commit message format: (e.g., Conventional Commits)
- When to open a PR and what to include in the description.
