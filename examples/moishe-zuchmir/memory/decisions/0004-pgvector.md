> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0004: PostgreSQL with pgvector instead of a dedicated vector database

- **Status:** accepted
- **Date:** 2026-03-02
- **Project:** ShidduchOps

## Context

Suggestions need similarity search over profile embeddings: about 600 profiles in the pilot, perhaps 50,000 one day. Every search is combined with hard filters (age range, region, the matchmaker's own pool), and withdrawing consent must delete a candidate's embeddings together with everything else, immediately.

## Decision

Store embeddings in the main PostgreSQL database with pgvector and an HNSW index. Filtering, joins and deletion happen in one query and one transaction.

## Alternatives considered

- **A dedicated vector database (hosted or self-hosted)**: one more system to run and secure, and a second copy of sensitive data that has to be kept in sync and deleted reliably.
- **An in-process index (such as FAISS)**: no persistence, no filtering, no transactions.

## Consequences

- One backup and one deletion path, which matters more here than raw speed.
- Revisit if the data passes about a million vectors, or if search quality or latency drops.
