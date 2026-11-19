# Contributing

Thanks for helping. one-memory stays small on purpose: Markdown, one issue form and one Claude Code skill. Changes that keep it that way are the easiest to accept.

## Good contributions

- Fixes to the platform guides when a product changes. Say what you saw, and when.
- Clearer wording in the protocol, the docs or the review skill.
- Guides for more assistants, as long as they fit the same read → propose → approve loop.

## Ground rules

- **No real personal data, ever**: not in issues, pull requests or examples. Use Moishe, or invent someone and mark them as fictional.
- **Only claim what you verified.** Platform guides carry a "Last checked" date. Say what you tested and on which plan, and mark the rest as unverified.
- **Keep the loop intact.** Assistants read and propose; only a review that a human approves changes memory. Changes that let assistants write memory directly won't be accepted.
- **No new moving parts without a strong reason.** Servers, scripts, tokens and GitHub Actions each add something to secure and maintain.

## Before you open a pull request

- Relative links work.
- Every file in `examples/` starts with the FICTIONAL DEMO DATA banner.
- `memory/` contains only the empty templates.

## Issues on this repository

The issue form here is the memory-proposal template that every copy receives. For bugs and ideas about the project itself, open a blank issue. For security problems, follow [SECURITY.md](SECURITY.md) instead.
