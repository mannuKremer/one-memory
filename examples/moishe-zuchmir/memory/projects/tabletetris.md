> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# TableTetris

- **Kind:** learning
- **Status:** paused (since 2026-09, until the ShidduchOps MVP ships)
- **My role:** solo
- **Stack:** Python 3.13, Google OR-Tools (CP-SAT solver), Typer for the command line
- **Started:** 2026-06

## What it is

A seating-chart optimizer. It assigns guests to tables while respecting constraints like "these two sit together", "these two never share a table" and "keep the kids' table away from the speakers". A weekend project for learning Python on a problem I already know well.

## Current state

- Seats 300 guests at 30 tables in under 5 seconds.
- Constraints come from a YAML file; the output is a CSV that hall staff can print.
- Paused on purpose: ShidduchOps comes first.

## Key decisions

None recorded. It's a learning project.

## Open questions

- Could this become KugelCloud's seating module? Product's answer so far: "after the Menu Assistant".
