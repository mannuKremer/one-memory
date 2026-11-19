> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# ShidduchOps

- **Kind:** side project
- **Status:** active (MVP)
- **My role:** solo builder
- **Stack:** Python 3.13, FastAPI, PostgreSQL 16 with pgvector, SQLAlchemy Core, Alembic, uv, pytest, Ruff, mypy; an LLM API behind a small provider-agnostic interface; Docker Compose on one small VM
- **Started:** 2026-01

## What it is

A case-management tool for professional matchmakers (shadchanim): candidate profiles, private notes, and a suggestion pipeline (suggested → checked → proposed → met → closed). Its AI layer suggests compatible profiles and explains each suggestion; the matchmaker decides. "Ops", because every shidduch is, at heart, a scheduling problem with feelings.

The two pilot matchmakers each manage about 300 profiles today, in spreadsheets and a paper notebook that has seen things.

## Current state

- Profiles, notes and the pipeline work end to end, on synthetic data only.
- Suggestions v1: hard filters, then pgvector similarity ([0004](../decisions/0004-pgvector.md)), then an LLM-written explanation for each suggestion ([0005](../decisions/0005-ai-suggests-matchmaker-decides.md)).
- Next: the golden-set evaluation gate ([0007](../decisions/0007-offline-eval-golden-set.md)), then the pilot, planned for March 2027.

## Privacy by design

- Candidates give recorded consent. Withdrawing it deletes their profile, notes and embeddings in one transaction.
- The model sees pseudonymized, structured attributes and notes with names and contact details stripped. Never photos.
- No automated contact with candidates, ever ([0005](../decisions/0005-ai-suggests-matchmaker-decides.md)).
- Evaluation uses synthetic profiles only. Real candidate data never goes into evaluation sets, logs or this memory.

## Key decisions

- [0003: Python and FastAPI instead of Spring Boot](../decisions/0003-python-fastapi-for-shidduchops.md)
- [0004: PostgreSQL with pgvector instead of a dedicated vector database](../decisions/0004-pgvector.md)
- [0005: The AI suggests, the matchmaker decides](../decisions/0005-ai-suggests-matchmaker-decides.md)
- [0007: A golden-set evaluation gate for suggestion changes](../decisions/0007-offline-eval-golden-set.md)

## Open questions

- How to measure a "good suggestion" beyond the matchmaker accepting it.
- Notes mix English, Hebrew and Yiddish. Which embedding model handles all three without favoring English?
- Whether fine-tuning is ever worth it. Only if evaluations show that prompting has plateaued.
