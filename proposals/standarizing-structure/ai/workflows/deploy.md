# Workflow: Deploy

> **Owner: Dev.** Pipeline and process for deploying to environments.

## Environments

| Environment | Purpose | Branch / Trigger | Approval |
|-------------|---------|------------------|----------|
| Development | Local or shared dev | (e.g., main, or feature branches) | Auto |
| Staging | Pre-production validation | (e.g., main, or release branch) | Auto |
| Production | Live users | (e.g., release tag or protected branch) | (e.g., manual or automated with gates) |

## Pipeline Steps

1. **Build**: Compile/transpile, run lint and unit tests. Fail fast on errors.
2. **Artifact**: Produce a versioned artifact (e.g., Docker image, package). Tag with commit SHA and/or version.
3. **Integration**: Run integration tests against a deployed dev/staging instance if applicable.
4. **Deploy to Staging**: Deploy artifact to staging; run smoke/E2E if defined.
5. **Deploy to Production**: After staging sign-off (and any manual approval), deploy to production.
6. **Post-deploy**: Health checks, smoke tests, and optional rollback procedure.

## Infrastructure

- IaC lives in `infrastructure/` (e.g., `terraform/`, `docker/`). See `.ai/ARCHITECTURE.md`.
- Changes to infrastructure are reviewed and applied via the same pipeline or a dedicated one; no ad-hoc changes to production.

## Rollback

- Document rollback steps (e.g., revert deploy, previous artifact, feature flags).
- Who can trigger rollback and how (e.g., CI action, runbook in `docs/`).

## Secrets and Config

- No secrets in repo; use secret manager or env injection per `.ai/SECURITY.md`.
- Config per environment (dev/staging/prod) is explicit and versioned where possible.

## Notifications

- Pipeline status (success/failure) is visible to the team (e.g., Slack, email).
- Production deploys are announced or logged for audit.
