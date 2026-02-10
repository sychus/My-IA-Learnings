# Feature: [FEAT-002] Payments

> **Owner: Product.** Human-defined spec. Complete feature specification.

## Summary

Users can initiate a payment (e.g., for a subscription or one-time purchase). The system integrates with a payment provider, records the transaction, and exposes status via API and optionally UI.

## Acceptance Criteria

- [ ] **AC1**: User can create a payment intent for a given amount and currency; required fields are validated.
- [ ] **AC2**: Payment status is stored and can be queried (e.g., pending, succeeded, failed, refunded).
- [ ] **AC3**: Idempotency: duplicate idempotency key for the same user/amount does not create a second charge.
- [ ] **AC4**: Failed payments are recorded with a reason; no silent failures.
- [ ] **AC5**: Sensitive payment data (e.g., full card number) is never stored; only provider tokens or last-four if needed for display.
- [ ] **AC6**: All payment-related actions are audited (who, when, amount, outcome).

## Out of Scope

- Full PCI scope (use a certified provider; we do not store raw card data).
- Subscription billing logic (recurring) in this feature; only one-off payment flow.
- Refund or dispute handling (separate feature).

## Domain / API

- **Domain**: See `specs/domain/models.md` — Payment, PaymentIntent (or equivalent).
- **API**: See `specs/api/openapi.yaml` — `POST /payments` (create), `GET /payments/:id` (status), idempotency key in header.
- New entities: Payment (id, user_id, amount, currency, status, provider_ref, idempotency_key, created_at, updated_at).

## UX / UI (if applicable)

- Payment form or redirect to provider; success and failure callback handling.
- User can see payment history and status (list and detail).

## Dependencies

- Chosen payment provider (e.g., Stripe, Adyen); credentials and config per SECURITY.md.
- Auth: only authenticated users can create or list their payments.
- Database for payment records.

## Notes

- Align with `.ai/SECURITY.md` for sensitive data and audit.
- Idempotency key format and lifetime should be documented in API spec.
