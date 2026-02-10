# Domain Models

> **Owner: Product.** Human-defined. Ubiquitous language and core entities. Keep in sync with `.ai/GLOSSARY.md`.

## Overview

This document describes the core domain entities, their attributes, and relationships. API and code should align with these models.

## Entities

### User

- **Purpose**: Represents an authenticated actor (person or system) in the application.
- **Attributes**:
  - `id`: Unique identifier (UUID).
  - `email`: Unique, used for login.
  - `password_hash`: One-way hash; never exposed.
  - `created_at`, `updated_at`: Timestamps.
- **Relations**: Has many Sessions; has many Payments (or other domain entities as needed).

### Session

- **Purpose**: Represents an authenticated session (e.g., after login).
- **Attributes**:
  - `id`: Unique identifier (UUID).
  - `user_id`: Reference to User.
  - `token_hash` (or equivalent): Stored token reference for validation.
  - `expires_at`: Session expiry.
  - `created_at`: When the session was created.
- **Relations**: Belongs to User.

### Payment

- **Purpose**: A single payment attempt or transaction.
- **Attributes**:
  - `id`: Unique identifier (UUID).
  - `user_id`: Who initiated the payment.
  - `amount_cents`: Amount in smallest currency unit.
  - `currency`: ISO 4217 (e.g., USD, EUR).
  - `status`: pending | succeeded | failed | refunded.
  - `provider_ref`: External payment provider reference (e.g., Stripe payment intent id).
  - `idempotency_key`: Client-provided key to prevent duplicate charges.
  - `created_at`, `updated_at`: Timestamps.
- **Relations**: Belongs to User. No sensitive card data stored.

## Invariants

- User email is unique and non-empty.
- Session must reference a valid User and must not be used after `expires_at`.
- Payment amount_cents > 0; currency is exactly 3 characters.
- Same (user_id, idempotency_key) must not create more than one successful charge.

## Optional Extensions

- **Tenant**: If multi-tenant, add Tenant entity and scope User/Payment by tenant_id.
- **Audit**: Consider an AuditLog or event table for sensitive actions (login, payment, etc.).
