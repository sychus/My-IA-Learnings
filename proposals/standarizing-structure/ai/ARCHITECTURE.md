# Architecture

> **Owner: Dev.** Human-written. Documents architectural decisions and system design.

## Overview

Describe the high-level architecture of the system (monolith, microservices, serverless, etc.) and the main bounded contexts.

## Principles

- **Principle 1**: (e.g., Domain-driven design, event-driven, API-first)
- **Principle 2**: (e.g., Fail-safe defaults, least privilege)
- **Principle 3**: (e.g., Stateless services, idempotent operations)

## Key Decisions

| Decision | Rationale | Date |
|----------|-----------|------|
| (Example: Use REST over GraphQL) | (Why) | YYYY-MM-DD |

## Diagrams

- Link or embed: C4 context diagram, deployment diagram, or other architecture diagrams.
- Keep in `docs/` or `docs/adr/` and reference here.

## Boundaries

- **Inbound**: How external systems or users interact with this system (APIs, events, UI).
- **Outbound**: How this system calls external services, databases, or message queues.
- **Data ownership**: Which services own which data; consistency and eventual consistency rules.

## Non-Goals (Out of Scope)

- What this system explicitly does *not* do, to avoid scope creep.
