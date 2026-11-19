> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Decisions

Lightweight decision records: one file per hard-to-reverse choice, numbered in order (`0001-<slug>.md`).

| # | Decision | Project | Status | Date |
|---|---|---|---|---|
| [0001](0001-modular-monolith.md) | Modular monolith instead of microservices | KugelCloud Booking Engine | accepted | 2025-02-10 |
| [0002](0002-transactional-outbox.md) | Transactional outbox for Kafka events | KugelCloud Booking Engine | accepted | 2025-06-03 |
| [0003](0003-python-fastapi-for-shidduchops.md) | Python and FastAPI instead of Spring Boot | ShidduchOps | accepted | 2026-01-18 |
| [0004](0004-pgvector.md) | PostgreSQL with pgvector instead of a dedicated vector database | ShidduchOps | accepted | 2026-03-02 |
| [0005](0005-ai-suggests-matchmaker-decides.md) | The AI suggests, the matchmaker decides | ShidduchOps | accepted | 2026-04-14 |
| [0006](0006-multi-vendor-order-saga.md) | Saga style for multi-vendor orders | KugelCloud Booking Engine | proposed | 2026-11-05 |
| [0007](0007-offline-eval-golden-set.md) | A golden-set evaluation gate for suggestion changes | ShidduchOps | accepted | 2026-11-17 |

- **Status:** proposed · accepted · superseded by NNNN · rejected
- New decision: copy `_template.md` to the next free number and add a row here.
