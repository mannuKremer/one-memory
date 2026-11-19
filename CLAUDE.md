# Working in this repository (Claude Code)

This is a one-memory repository: Markdown memory files that AI assistants read and propose changes to. The rules are in `PROTOCOL.md`.

- Change files under `memory/` only while running `/memory-review`, or when the user explicitly asks you to edit memory in this session (for example, the first fill-in described in `docs/MAKE-IT-YOURS.md`). Outside `/memory-review`, show the diff and don't commit unless the user asks.
- `examples/` is fictional demo data. Never copy facts from it into `memory/`.
- Never write anything from the "Never store" list in `PROTOCOL.md` section 4, even when asked in passing. Say why instead.
