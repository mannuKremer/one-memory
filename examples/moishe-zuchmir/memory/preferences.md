> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Preferences

## Engineering

- Boring technology first. A new tool has to replace something, not just join it.
- PostgreSQL until proven otherwise: constraints, transactions and its own search features before any new datastore. Postgres is the cast-iron pot of databases.
- Every Kafka consumer is idempotent. Rule #2: see rule #1. It may have been delivered twice.
- Make illegal states unrepresentable: database constraints and explicit types over runtime checks.
- Plain SQL, or a thin query builder, for anything non-trivial. No ORM that hides the query.
- Integration tests with Testcontainers rather than a mocked database.
- A decision record for anything that is hard to reverse.

## Code style and review

- Small pull requests, under about 400 changed lines, because reviews happen between meetings.
- Review comments are labeled **blocking**, **suggestion** or **nit**.
- Names over comments. Comments explain *why*.
- No annotation magic in domain code (Lombok stays out of there).

## Working with AI assistants

- Answer first, details after. Code first, then the explanation.
- Trade-offs in a table, with a recommendation.
- For Python: flag the Java habits in my code (getters, factories of factories, a class where a function would do) and show the idiomatic version.
- When suggesting a library, say how mature it is and what it replaces.
- Push back when I'm wrong. No flattery, no apologies.

## Communication

- Direct and concise. Examples from the catering domain land best.
- Puns are tolerated, one per answer.
