> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0003: Python and FastAPI instead of Spring Boot

- **Status:** accepted
- **Date:** 2026-01-18
- **Project:** ShidduchOps

## Context

ShidduchOps has two goals: help real matchmakers, and teach me Python and AI engineering. In Spring Boot it would ship faster at first. But the AI tooling (embedding libraries, evaluation frameworks, SDK examples) is Python-first.

## Decision

Build it in Python 3.13 with FastAPI, SQLAlchemy Core (no ORM), Alembic, uv, pytest, Ruff and mypy in strict mode.

## Alternatives considered

- **Spring Boot with Spring AI**: the fastest start, and it defeats the learning goal.
- **TypeScript on Node.js**: a third ecosystem to learn, without the AI-tooling advantage.

## Consequences

- Slower first months, and a real risk of Java-flavored Python. Mitigation: Ruff, mypy, and asking assistants to point out Java habits.
- SQLAlchemy Core keeps the SQL visible (see `preferences.md`). Alembic plays the role that Flyway plays at work.
- What I learn here feeds the Menu Assistant at KugelCloud.
