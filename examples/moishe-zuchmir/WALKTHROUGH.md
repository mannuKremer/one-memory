> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# Walkthrough: from conversation to commit

One full loop through Moishe's memory: a conversation in ChatGPT, a proposal, a GitHub issue, `/memory-review` in Claude Code, a commit, and a different assistant that knows the result the next day. Issue numbers, commit hashes and timings are illustrative.

In Moishe's own private repository, his memory lives in `memory/`. Here it lives in [memory/](memory/core.md), and it already contains the result of this walkthrough.

## 1. The conversation (ChatGPT, 2026-11-17)

Moishe uses a ChatGPT Project set up with the instructions from [docs/platforms/chatgpt.md](../../docs/platforms/chatgpt.md). ChatGPT's GitHub app can read his memory repository, but it can't create issues.

> **Moishe:** I tweaked the ShidduchOps prompt yesterday, and the suggestions for one of my test candidates got noticeably worse. Nothing caught it. How do I stop evaluating by vibes?
>
> **ChatGPT:** *(reads `memory/core.md`, `projects/shidduchops.md` and decision 0005 through the GitHub app)* You already have something most teams lack: under 0005, matchmakers accept or reject every suggestion with a reason. That's labeled data, but you can't test on real candidates. Three options:
>
> | Option | Catches regressions before release | Cost | Risk |
> |---|---|---|---|
> | Manual spot checks | Rarely | Your evenings | It's what just failed |
> | Golden set and metrics in CI | Yes | A day to build, a few dollars per run | Synthetic data drifts from reality |
> | Online A/B tests with the pilot matchmakers | Too late | Nothing extra | Two users, and real people on the other end |
>
> I'd build a golden set: synthetic profiles, pairs labeled by your two pilot matchmakers, precision@5 for ranking, and an LLM judge for the explanations. Gate every prompt, model or ranking change on it in CI.
>
> **Moishe:** Agreed. 40 synthetic profiles. A change ships only if precision@5 doesn't drop and the judge prefers the new version at least half the time. I'll hand-check 10% of the judge's calls.
>
> **Moishe:** Unrelated: I finished the pytest chapter. Fixtures finally make sense. It's as if `@BeforeEach` and dependency injection had a baby.
>
> **Moishe:** Also, remind me never to buy an office chair online again. My back is killing me.
>
> **Moishe:** Remember the eval decision and the pytest thing.

## 2. The proposal

ChatGPT has no tool for creating issues, so it follows the fallback in [PROTOCOL.md](../../PROTOCOL.md#5-how-to-propose):

> **ChatGPT:** I can't open issues from here, so here's the proposal to paste. I left out the chair and your back: health stays out of memory.
>
> *(one code block containing the body below)*
>
> Paste it here: `https://github.com/…/issues/new?template=memory-proposal.yml`

Moishe clicks the link, replaces the example text with the block, ticks the privacy box and submits. It becomes **issue #14**, `[memory] ShidduchOps eval gate and pytest progress`:

````markdown
### Change 1
- **File:** `memory/decisions/0007-offline-eval-golden-set.md`
- **Action:** add
- **Why:** Defines how every future prompt, model or ranking change in ShidduchOps is judged.

**After**
~~~markdown
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
~~~

### Change 2
- **File:** `memory/learning.md`
- **Action:** update
- **Why:** Python progress: pytest is now usable in ShidduchOps, and async is next.

**Before**
~~~text
| Python 3.13 (typing, pytest, uv) | ShidduchOps, Menu Assistant | Writing services; tests still feel like JUnit with extra steps | Finish the pytest fixtures chapter |
~~~

**After**
~~~markdown
| Python 3.13 (typing, async, uv) | ShidduchOps, Menu Assistant | Writing services; pytest fixtures finally clicked ("`@BeforeEach` and dependency injection had a baby") | async/await: port the suggestion endpoint to async |
~~~

---
- **Source:** chatgpt
- **Date:** 2026-11-17
- **Privacy check:** professional only, nothing from PROTOCOL.md section 4
````

The office chair is nowhere in it.

With Claude.ai and the GitHub connector ([docs/platforms/claude-ai.md](../../docs/platforms/claude-ai.md)), this step is a single approval click: Claude opens the issue itself and replies with the link.

## 3. The review (Claude Code, 2026-11-18)

```bash
cd ~/my-memory && claude
```

Moishe types `/memory-review`. Claude Code runs the preflight (clean tree on `main`, pull, `gh` logged in, repository private), reads the issue and the target files, and answers:

> One open proposal.
>
> | Issue | Change | File | Action | Summary | Source | Recommendation |
> |---|---|---|---|---|---|---|
> | #14 | 1 | `memory/decisions/0007-offline-eval-golden-set.md` | add | Golden-set evaluation gate for ShidduchOps | chatgpt | **Apply.** Follows the template; 0007 is the next free number. |
> | #14 | 2 | `memory/learning.md` | update | Python row: pytest done, async next | chatgpt | **Apply.** The `Before` text matches exactly. |
> | #14 | related | `memory/projects/shidduchops.md` | update | "Next" still says "decide how to evaluate suggestions"; point it at 0007 | review | **Apply**, if you agree. |
>
> Checks: the author is the repository owner, every path is inside `memory/`, and nothing matches the "Never store" list.
> If you approve 0007, I'll also add it to `decisions/index.md`, link it from the ShidduchOps project file, and update `core.md`.
>
> How should I proceed? For example `apply all`, `reject 14.2` or `edit 14.2: …`

> **Moishe:** apply all. For 14.2, also add pytest to the Done list. Commit and push when you're done.

Claude Code applies the changes and shows the diff:

```text
 memory/core.md                                   |  4 +-
 memory/decisions/0007-offline-eval-golden-set.md | 27 +++++
 memory/decisions/index.md                        |  1 +
 memory/learning.md                               |  3 +-
 memory/projects/shidduchops.md                   |  3 +-
 5 files changed, 34 insertions(+), 4 deletions(-)
```

Moishe already said "commit and push", so it doesn't ask again:

```text
$ git commit -m "memory: apply #14"
[main 3f9c2ab] memory: apply #14
$ git push
$ gh issue close 14 --reason completed --comment "Applied in commit 3f9c2ab."
✓ Closed issue #14
```

> Applied #14: decision 0007, the Python learning update (plus pytest under Done) and the ShidduchOps next step. Nothing rejected, nothing left open.

The git history is the audit log:

```text
$ git log --oneline -3 -- memory/
3f9c2ab memory: apply #14
8d41e07 memory: apply #11, #12
1a7b3c9 memory: apply #9
```

## 4. The next assistant knows (Claude.ai, 2026-11-19)

Moishe opens Claude.ai, which reads his memory through the GitHub connector:

> **Moishe:** Should I switch the ShidduchOps explanations to a cheaper model?
>
> **Claude:** *(reads `memory/core.md` and decision 0007)* Run it through your golden-set gate first (0007). Only the explanations change, so precision@5 should hold. The deciding number is the judge: the cheaper model has to be preferred at least half the time. And at about a fifth of a cent per explanation (0005), check that the savings are worth the evaluation run at all.

Nobody copied anything between assistants, and nothing entered memory without Moishe's approval.

## What this shows

- **Privacy is filtered at the source.** The back pain never reached the issue, let alone the memory.
- **A human stays in charge.** Moishe approved every change, extended one, and could have rejected any of them.
- **One fact, one place.** The review kept the index, the project file and `core.md` consistent.
- **Honest fallbacks.** ChatGPT couldn't write, said so, and the loop still cost Moishe about 15 seconds.
- **Git is the audit log.** Every change has a commit, an issue and a reason.
