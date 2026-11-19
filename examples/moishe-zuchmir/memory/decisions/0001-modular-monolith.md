> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0001: Modular monolith instead of microservices

- **Status:** accepted
- **Date:** 2025-02-10
- **Project:** KugelCloud Booking Engine

## Context

"Cholent", the 2019 monolith, had become one tangled package graph: a change to deposits could break seating. The proposal on the table was to split it into nine microservices. KugelCloud has 14 engineers, one platform engineer and one PostgreSQL cluster, and the most important rule in the system (no double bookings, deposits always match contracts) would span three of those services.

## Decision

Restructure into a modular monolith with Spring Modulith. Each module owns its tables (one schema per module) and talks to other modules only through published application events or a small public API. Module boundaries are verified in CI. One deployable.

## Alternatives considered

- **Nine microservices**: more operational load than the team can carry, plus distributed transactions around bookings and payments.
- **Keep the monolith as it is**: deploys were fine; the coupling was not, and it was getting worse.

## Consequences

- Boundaries are enforced by tests instead of by the network.
- A module can still be extracted later if it needs to scale on its own. Kitchen Planning in wedding season is the first candidate.
- The database is shared, so cross-module queries are forbidden by convention and caught in review. That takes discipline.
- Revisit when a module needs independent scaling or its own release cadence.
