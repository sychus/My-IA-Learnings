# API patterns (Dev skill)

> **Owner: Dev.** Patterns agents should follow when implementing or changing API endpoints.

- Implement against `specs/api/openapi.yaml`; do not deviate without updating the spec and logging in `decisions-log.md`.
- Use standard HTTP status codes: 2xx success, 4xx client error, 5xx server error. Avoid custom codes.
- Validate request body and query params; return 400 with a clear validation message.
- For errors, return a consistent JSON shape (e.g. `{ "error": { "code": "...", "message": "..." } }`).
- Idempotency: support `Idempotency-Key` header where the spec requires it; store and reuse response for duplicate keys.

Agents (coder, reviewer) should align all API changes with this and with `CONVENTIONS.md` and `ARCHITECTURE.md`.
