> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0002: Transactional outbox for Kafka events

- **Status:** accepted
- **Date:** 2025-06-03
- **Project:** KugelCloud Booking Engine

## Context

Booking events were written to PostgreSQL and then sent to Kafka in a separate step. During a Kafka outage in May 2025, a booking was rolled back after its "booking confirmed" event had already gone out, and a caterer started planning a 220-guest dinner that no longer existed. The opposite happened too: committed bookings whose events never left. A classic dual write.

## Decision

Write every event to an `outbox` table in the same transaction as the business change. A polling publisher sends outbox rows to Kafka and marks them as sent. Consumers deduplicate by event ID, using a processed-events table in their own schema.

## Alternatives considered

- **Kafka transactions**: they don't cover the PostgreSQL commit, which is the actual problem.
- **Change data capture (Debezium)**: sturdier at scale, but another system to run, for about 40 events per second at peak. Revisit above roughly 500 per second.
- **Publish first, then commit**: moves the failure to the other side.

## Consequences

- Delivery is at least once, so every consumer must be idempotent (rule #1 in `preferences.md`).
- Publishing adds about one second of latency, which is fine for bookings.
- The outbox needs a cleanup job: sent rows are deleted after seven days.
