> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Example: Moishe Zuchmir

A complete, fictional one-memory, so you can see what a filled-in memory looks like before you write your own.

## Who is Moishe?

Moishe Zuchmir is a senior backend engineer at **KugelCloud**, a startup whose SaaS runs catering companies and event halls: bookings, menus, guest counts, seating and kitchen production. He has spent eleven years making sure that things which must happen exactly once happen exactly once (payments first, now weddings), and he believes every system eventually becomes either a queue or a spreadsheet. He prefers the queue.

He is learning Python and AI engineering. His side project, **ShidduchOps**, helps professional matchmakers manage their candidates, with AI suggestions that the matchmaker always has the final word on. He uses ChatGPT to think things through and Claude Code to build.

## What's here

| Path | What it shows |
|---|---|
| [memory/core.md](memory/core.md) | A complete core file, well under 60 lines, with its `read_check` |
| [profile](memory/profile.md), [goals](memory/goals.md), [preferences](memory/preferences.md), [learning](memory/learning.md) | Topic files |
| [memory/projects/](memory/projects/index.md) | Four projects in different states: active, idea, paused |
| [memory/decisions/](memory/decisions/index.md) | Seven decision records, including an open dilemma (0006) |
| [WALKTHROUGH.md](WALKTHROUGH.md) | The full loop: conversation → proposal → issue → review → commit |

The `_template.md` files are left out here. They live in the top-level `memory/` folder.

## Worth noticing

- **Reasons, not just facts.** "PostgreSQL until proven otherwise" comes with its reasons ([0004](memory/decisions/0004-pgvector.md)).
- **Privacy in the content itself.** ShidduchOps handles very sensitive data. The memory describes how that data is protected without containing any of it.
- **Open questions are memory too.** Decision [0006](memory/decisions/0006-multi-vendor-order-saga.md) is still only proposed, so assistants know not to treat it as settled.
- **A small core, deep topics.** `core.md` summarizes and points to everything else.

## Using it

This folder is read-only reference material. PROTOCOL.md tells assistants never to treat it as facts about you, and `/memory-review` never changes it. To use it as a style guide for your own memory, see [docs/MAKE-IT-YOURS.md](../../docs/MAKE-IT-YOURS.md).
