# Claude Code

Claude Code is the one required piece: it runs `/memory-review`, the approval step. It can also read your memory and propose changes from any project you work on.

| | How |
|---|---|
| Read | An `@` import of `core.md` in your user-level `CLAUDE.md` |
| Propose | `gh issue create` |
| Approve | `/memory-review`, inside your memory clone |

_Last checked: November 2026._

## 1. Load the memory in your sessions

Add this to `~/.claude/CLAUDE.md` (create the file if it doesn't exist). Change `~/my-memory` if you cloned somewhere else.

```markdown
# Professional memory (one-memory)

@~/my-memory/memory/core.md

- This is my shared professional memory. Follow ~/my-memory/PROTOCOL.md.
- Read other files in ~/my-memory/memory/ only when the topic needs them.
- To propose a change, pass the PROTOCOL.md body through a quoted heredoc:
  gh issue create -R YOUR_USER/YOUR_MEMORY_REPO --label memory-proposal --title "[memory] <summary>" --body-file -
- Edit files in ~/my-memory/memory/ only during /memory-review.
```

The `@` line imports `core.md` into Claude Code's context when a session starts. The first time, Claude Code may ask you to approve the import. Confirm that it works with Test 1 in [VERIFY.md](../VERIFY.md).

Good to know:

- It reads your **local clone**. `/memory-review` pulls before every review. If you change the memory from another machine, run `git pull` here.
- A session that is already running keeps the version it started with.
- Claude Code drops YAML frontmatter from imported files. That's why `core.md` keeps `last_updated` and `read_check` in its body: leave them there.

## 2. Review proposals

```bash
cd ~/my-memory && claude
```

Then type `/memory-review`. It is a project skill, so it exists only inside this repository, and only you can start it: Claude won't run it on its own.

It checks each open proposal (allowed path, privacy, author, duplicates, exact `Before` text), shows one table with recommendations, applies only what you approve, shows the diff, commits and pushes after you agree, and closes the issues with a comment.

## Permissions

- `gh` acts as you, with your own login. No extra tokens are needed.
- The skill pre-approves read-only commands only (`git status`, `git diff`, `git log`, `gh issue list`, `gh issue view`, `gh repo view`). Editing files, committing, pushing and closing issues go through Claude Code's normal permission prompts.

## Limitations

- Claude Code's own memory features (`CLAUDE.md` files, auto memory) keep working independently. one-memory doesn't sync with them.
- Claude Code only sees what you imported or what it reads with its tools. Topic files are read on demand, when Claude decides the topic needs them.
