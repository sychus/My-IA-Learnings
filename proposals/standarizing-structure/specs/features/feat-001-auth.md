# Feature: [FEAT-001] Authentication

> **Owner: Product.** Human-defined spec. Complete feature specification.

## Summary

Users can sign up, sign in, and sign out. Sessions are managed via secure, HTTP-only cookies or tokens. Passwords meet a defined policy and are stored hashed.

## Acceptance Criteria

- [ ] **AC1**: User can register with email and password; email is validated and must be unique.
- [ ] **AC2**: User can sign in with email and password; invalid credentials return a generic error (no user enumeration).
- [ ] **AC3**: User can sign out; session is invalidated.
- [ ] **AC4**: Password policy: minimum length, complexity (e.g., upper, lower, number, symbol) as defined in config.
- [ ] **AC5**: Passwords are stored using a strong one-way hash (e.g., bcrypt/argon2); never stored or logged in plain text.
- [ ] **AC6**: Session has a configurable timeout; expired sessions require re-authentication.
- [ ] **AC7**: Protected routes return 401 when the user is not authenticated.

## Out of Scope

- Social login (OAuth) in this feature.
- Password reset or email verification (separate features).
- Multi-factor authentication (MFA).

## Domain / API

- **Domain**: See `specs/domain/models.md` — User, Session (or equivalent).
- **API**: See `specs/api/openapi.yaml` — `POST /auth/register`, `POST /auth/login`, `POST /auth/logout`, `GET /auth/me` (or equivalent).
- New entities: User (id, email, password_hash, created_at, updated_at), Session (id, user_id, token_hash, expires_at).

## UX / UI (if applicable)

- Registration form: email, password, confirm password.
- Login form: email, password.
- Logout: button or link that calls logout and redirects.
- Clear error messages for validation; generic message for invalid login.

## Dependencies

- Database for users and sessions.
- Config for password policy and session TTL.
- No dependency on other application features.

## Notes

- Align with `.ai/SECURITY.md` for auth and session handling.
- Consider rate limiting on login/register in a later iteration.
