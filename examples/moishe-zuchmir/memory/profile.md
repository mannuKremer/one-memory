> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Profile

## Summary

Backend engineer who has spent eleven years making sure that things which must happen exactly once happen exactly once: payments, shipments, and now weddings. Strongest in Java, PostgreSQL and Kafka; happiest designing data models and failure handling. Currently adding Python and applied AI to the toolbox.

## Experience

| Period | Role | Where | Highlights |
|---|---|---|---|
| 2021 to now | Senior Backend Engineer | KugelCloud (SaaS for caterers and event halls) | Owns Booking & Orders. Led the move to a modular monolith and the transactional outbox. No double bookings since holds moved to a PostgreSQL exclusion constraint. Leads the on-call guild. |
| 2018 to 2021 | Backend Engineer | A payments startup | Spring Boot and Kafka services for payouts and reconciliation. Learned that "exactly once" is a promise you keep in the consumer, not in the broker. |
| 2015 to 2018 | Java Developer | A logistics software company | Java EE and Oracle, warehouse integrations. Learned that every warehouse runs on one spreadsheet that nobody is allowed to touch. |

## Skills

- **Strong:** Java 21, Spring Boot 3, PostgreSQL (query tuning, partitioning, constraints), Kafka (consumer groups, idempotent consumers, outbox), domain-driven design, Testcontainers, Flyway, OpenTelemetry.
- **Working knowledge:** Kubernetes, Terraform, AWS, Redis, and enough TypeScript to review frontend pull requests.
- **Learning:** Python and AI engineering, see `learning.md`.

## Domains

- Booking systems with hard capacity limits: halls, time slots, deposits
- Payments, payouts and reconciliation
- Multi-tenant B2B SaaS
- Event logistics: menus, guest counts, kitchen production planning
