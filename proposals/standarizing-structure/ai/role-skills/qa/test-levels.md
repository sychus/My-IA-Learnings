# Test levels (QA skill)

> **Owner: QA.** When to use each test level so agents add the right tests.

- **Unit**: New or changed business logic; edge cases and validation. Mock external deps. Fast; run on every commit.
- **Integration**: New or changed API endpoints or DB usage; contracts and workflows. Use real DB or test doubles as agreed. Stable; run in CI.
- **E2E**: Critical user journeys only (e.g. sign-up → first use). Expensive; run on main or before release. Do not duplicate unit/integration coverage here.

For every new feature, at least one acceptance criterion should be covered by unit or integration tests. E2E is optional unless the feature spec or QA explicitly requires it.
