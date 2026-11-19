> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# 0005: The AI suggests, the matchmaker decides

- **Status:** accepted
- **Date:** 2026-04-14
- **Project:** ShidduchOps

## Context

Suggesting two people to each other is personal and high-stakes. Language models can be confidently wrong, and they can carry bias. And the matchmaker's reputation is the product: one careless suggestion can cost trust that took years to build.

## Decision

- ShidduchOps never contacts candidates and never shares a profile on its own. Every outbound step is a human action.
- Every suggestion shows its reasons: which attributes matched and which notes it relied on.
- The matchmaker accepts or rejects each suggestion, with a short reason.
- Rejections and their reasons are kept for evaluation, never for automatic retraining.
- The model sees only pseudonymized, structured attributes, and notes with names and contact details stripped.

## Alternatives considered

- **Send the top matches to candidates automatically**: fast, and exactly how a matchmaker loses their good name.
- **A ranked list without explanations**: the matchmaker can't check the reasoning, so they can't trust it.

## Consequences

- Slower than full automation, on purpose.
- Explanations cost tokens, about a fifth of a cent per suggestion. Acceptable.
- A complete audit trail of who decided what, and why.
- It is the same rule this memory runs on: assistants propose, a human approves.
