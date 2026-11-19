# Make it yours

`memory/` starts empty. This guide fills it with your own professional context. To see what a filled-in memory looks like, browse the fictional example in [examples/moishe-zuchmir/memory](../examples/moishe-zuchmir/memory/core.md).

## Guidelines

- **Professional only.** Nothing from the "Never store" list in [PROTOCOL.md](../PROTOCOL.md#4-never-store).
- **Write for a smart stranger.** Short bullets an assistant can act on: "prefers PostgreSQL unless proven otherwise", not "likes databases".
- **Give reasons.** "Small PRs, because reviews happen between meetings" helps more than "small PRs".
- **One fact, one place.** Details live in topic files. `core.md` only summarizes, in 60 lines or fewer.
- **Start small.** A thin memory that is correct beats a thick one that is stale. It grows through proposals.

## Option A: an interview with Claude Code (recommended)

Open Claude Code in your clone (`cd ~/my-memory && claude`) and paste:

```text
Help me fill in my one-memory for the first time.
Read PROTOCOL.md and the empty files in memory/. Use examples/moishe-zuchmir/memory/ only as a style reference: it is fictional, so copy no facts from it.
Interview me one file at a time, in this order: profile, goals, preferences, learning, projects, decisions. Ask at most 3 questions per message and accept "skip".
Write only professional facts. If I mention anything from PROTOCOL.md section 4, leave it out and tell me.
After each file, show me what you wrote. At the end, write core.md (60 lines or fewer), set last_updated to today and read_check to a new random word, and show me git diff. Don't commit.
```

Read the diff, then commit:

```bash
git add memory && git commit -m "memory: first version" && git push
```

## Option B: by hand

Fill in the files in this order. Each one has short guidance comments inside.

| File | What goes in | Fictional example |
|---|---|---|
| `memory/profile.md` | Experience, skills, domains | [profile.md](../examples/moishe-zuchmir/memory/profile.md) |
| `memory/goals.md` | 12-month goals, longer term, explicit non-goals | [goals.md](../examples/moishe-zuchmir/memory/goals.md) |
| `memory/preferences.md` | How you like to work, review and be helped | [preferences.md](../examples/moishe-zuchmir/memory/preferences.md) |
| `memory/learning.md` | What you're learning, how far you got, what's next | [learning.md](../examples/moishe-zuchmir/memory/learning.md) |
| `memory/projects/` | One file per project, from `_template.md`, plus a row in `index.md` | [projects](../examples/moishe-zuchmir/memory/projects/index.md) |
| `memory/decisions/` | One file per hard-to-reverse decision, plus a row in `index.md` | [decisions](../examples/moishe-zuchmir/memory/decisions/index.md) |
| `memory/core.md` (last) | Summary, current focus, projects, top preferences | [core.md](../examples/moishe-zuchmir/memory/core.md) |

In `core.md`, delete the "This memory is empty" line, set `last_updated` to today and set `read_check` to any random word, such as `blue-falafel-7`.

## Optional: start from what your assistants already know

Ask ChatGPT or Claude: "List everything you remember about my professional background, projects and preferences, as bullets." Paste the answer into the Option A interview as raw material. Read it first: built-in memories often hold personal details that don't belong here.

## Before you commit

- [ ] The repository is private: `gh repo view --json visibility --jq .visibility` prints `PRIVATE`.
- [ ] `wc -l memory/core.md` prints 60 or less.
- [ ] You read `git diff`: no secrets and nothing from the "Never store" list.
- [ ] No demo facts slipped in: `grep -rniE 'zuchmir|kugelcloud|shidduchops' memory/` prints nothing.

## Optional cleanup

Once you no longer need the example, you can delete it from your copy so that it never shows up when an assistant searches the repository. Links to it from the docs will stop working, which is fine.

```bash
git rm -r examples && git commit -m "Remove the demo example" && git push
```
