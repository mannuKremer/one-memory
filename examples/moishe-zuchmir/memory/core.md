> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Core memory: Moishe Zuchmir

- **last_updated:** 2026-11-18
- **read_check:** potato-kugel-42

## Who I am

Senior Backend Engineer at KugelCloud, a SaaS for caterers and event halls. About 11 years of Java backends (Spring Boot, PostgreSQL, Kafka); I own the Booking & Orders domain. Learning Python and AI engineering, aiming to lead AI features at work.

## Current focus

- Moving Booking and Orders out of the "Cholent" monolith into proper modules ([0001](decisions/0001-modular-monolith.md)).
- ShidduchOps MVP for two pilot matchmakers: building the evaluation gate next ([0007](decisions/0007-offline-eval-golden-set.md)).
- Getting from "Python that I compile in my head as Java" to idiomatic Python.

## Projects

| Project | Role | Status | File |
|---|---|---|---|
| KugelCloud Booking Engine | Tech lead, Booking & Orders | active | [kugelcloud-booking-engine.md](projects/kugelcloud-booking-engine.md) |
| ShidduchOps | Solo builder (side project) | active, MVP | [shidduchops.md](projects/shidduchops.md) |
| Menu Assistant | Proposer (work) | idea, pitched | [menu-assistant.md](projects/menu-assistant.md) |
| TableTetris | Solo (learning) | paused | [tabletetris.md](projects/tabletetris.md) |

## How to work with me

- Answer first, details after. Put trade-offs in a table, with a recommendation.
- Boring technology first. PostgreSQL until proven otherwise.
- Every Kafka consumer is idempotent. (Rule #2: see rule #1. It may have been delivered twice.)
- In Python, flag my Java habits (getters, factories of factories) and show the idiomatic version.
- Push back when I'm wrong. Skip the compliments.

## Memory map

| File | Read it when |
|---|---|
| `memory/profile.md` | experience, skills, domains |
| `memory/goals.md` | career direction and priorities |
| `memory/preferences.md` | how I like to work and communicate |
| `memory/learning.md` | what I'm learning now |
| `memory/projects/index.md` | any project question, then the project's own file |
| `memory/decisions/index.md` | "why did we choose X?", then the decision's own file |
