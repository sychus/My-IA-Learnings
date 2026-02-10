# Security

> **Owner: Dev.** Human-written. Security policies, boundaries, and practices.

## Security Principles

- **Least privilege**: Services and users get only the permissions they need.
- **Defense in depth**: Multiple layers (network, app, data).
- **Secure by default**: Safe defaults; opt-in for risky features.
- **No secrets in code**: Use secret managers, env, or vaults.

## Trust Boundaries

- **Public**: Unauthenticated or low-trust (e.g., landing, login).
- **Authenticated**: After login; still tenant/user scoped.
- **Internal**: Service-to-service; not exposed to the internet.
- **Admin**: Highest privilege; audit everything.

## Data Classification

- **Public**: Can be shared openly.
- **Internal**: Not for external sharing.
- **Confidential**: PII, business-sensitive; encrypt at rest and in transit.
- **Restricted**: Compliance-sensitive; access logged and limited.

## Authentication & Authorization

- How users and services authenticate (e.g., OAuth2, JWT, API keys).
- How authorization is enforced (e.g., RBAC, ABAC, resource-level).
- Session and token lifetime, refresh, revocation.

## Input Validation & Injection

- Validate and sanitize all inputs (API, UI, files).
- Use parameterized queries / ORM; no raw concatenation for SQL or commands.
- Content-Type and size limits for uploads.

## Dependency & Supply Chain

- Lockfile and reproducible builds.
- Automated dependency scanning (e.g., Dependabot, Snyk).
- Policy for responding to CVEs.

## Incident Response

- Who to contact and how (e.g., security@, Slack channel).
- Steps for suspected breach or vulnerability disclosure.
- Post-incident: blameless review and runbook updates.
