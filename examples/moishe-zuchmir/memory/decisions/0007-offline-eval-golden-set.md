> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0007: A golden-set evaluation gate for suggestion changes

- **Status:** accepted
- **Date:** 2026-11-17
- **Project:** ShidduchOps

## Context

A small prompt change made the suggestions for one test candidate noticeably worse, and nothing caught it. Until now, evaluation meant reading a few outputs and deciding they looked fine. Real candidates can't be used for testing, and two pilot matchmakers are too few users for online experiments.

## Decision

- Build a golden set: 40 synthetic candidate profiles, with good and bad pairs labeled by the two pilot matchmakers.
- Measure ranking with precision@5 against the labeled pairs, and explanations with an LLM judge that compares each new version with the current one, using a written rubric.
- Run it in CI on every change to prompts, model or ranking code.
- A change ships only if precision@5 doesn't drop and the judge prefers the new version at least half the time.

## Alternatives considered

- **Manual spot checks**: what I did until now. It missed this regression.
- **Online A/B tests with the pilot matchmakers**: too few users, and real people on the receiving end.

## Consequences

- The synthetic set needs upkeep as features change.
- LLM judges have biases of their own, so I hand-check 10% of their calls.
- A few dollars per evaluation run.
