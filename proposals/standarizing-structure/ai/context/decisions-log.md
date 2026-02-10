# Decisions Log

> **Owner: Dev.** Append-only log of significant decisions. For full ADRs, see `docs/adr/`.

Format: one entry per decision, newest at the top.

---

## YYYY-MM-DD — Short title

**Context**: What was the situation or question?  
**Decision**: What was decided?  
**Rationale**: Why (brief).  
**Consequences**: What we need to do or remember (e.g., update STACK, add test).

---

## (Example) 2025-01-15 — Use PostgreSQL for primary data

**Context**: Need a primary store for user and transaction data.  
**Decision**: Use PostgreSQL 15+.  
**Rationale**: ACID, JSON support, team experience, and managed offerings available.  
**Consequences**: All new features assume PostgreSQL; document connection and migration strategy in ARCHITECTURE.

---

(Add new entries above this line.)
