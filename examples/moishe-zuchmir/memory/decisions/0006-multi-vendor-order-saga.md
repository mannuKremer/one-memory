> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0006: Saga style for multi-vendor orders

- **Status:** proposed
- **Date:** 2026-11-05
- **Project:** KugelCloud Booking Engine

## Context

A single event order now involves up to five parties: the hall, the caterer, the florist, the photographer and the DJ. Each one confirms or declines asynchronously, sometimes days later. When one declines, or the guest count changes after vendors have confirmed, other steps must be compensated: release the hold, resize the menu, tell the florist. Today this logic lives in if-statements and in one support engineer's head.

## Decision

Not decided yet. Leaning towards C. A two-week spike in December 2026 will compare C and A on the hardest scenario: the guest count changes after three vendors have already confirmed.

## Alternatives considered

| Option | For | Against |
|---|---|---|
| **A. Orchestration with a workflow engine** (such as Temporal) | Explicit flow, durable timers and retries, good visibility | New infrastructure. Breaks "boring technology first" unless it replaces something |
| **B. Choreography over Kafka** (the existing outbox, 0002) | No new infrastructure; modules stay decoupled | The flow is implicit, and "where is order 4512?" turns into archaeology |
| **C. A state machine in the Orders module**, persisted in PostgreSQL | Boring, explicit, fits 0001 | Home-grown timers and retries that must be built carefully |

## Consequences

- Until this is decided, new multi-vendor features wait.
- Whichever option wins, the outbox (0002) stays the only way events leave the database.
