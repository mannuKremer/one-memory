> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Menu Assistant

- **Kind:** work
- **Status:** idea (pitched to the CTO in October 2026; a decision is expected in January 2027)
- **My role:** proposer, and tech lead if it's approved
- **Stack:** not decided, see open questions
- **Started:** 2026-10

## What it is

Turns a client's free-text request into a draft menu, quantities and quote, based on the caterer's own menu catalog and past events. A typical request: "Like last spring's gala dinner, but 40 more guests, and half of them vegan."

## Current state

- A two-page proposal and a prototype running on anonymized demo data.
- Design rule: the LLM picks dishes, arithmetic stays in code. Quantities and prices come from the existing kitchen-planning logic, never from the model.
- Allergen and dietary information comes only from catalog data. The assistant never decides on its own that a dish is allergen-free.

## Key decisions

None yet.

## Open questions

- Java (Spring AI) inside the monolith, or a small Python service next to it? I'd enjoy the Python; the team knows Java. Leaning: prototype in Python, production in Java, unless the evaluation tooling makes Python clearly better.
- Strict tenant isolation in retrieval: one caterer's past events must never shape another caterer's quote.
