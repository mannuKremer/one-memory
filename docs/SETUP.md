# Setup

About 15 minutes. At the end you have a private memory repository that you own, Claude Code ready to review proposals, and, if you want them, Claude.ai and ChatGPT connected.

## What you need

- A GitHub account
- `git` and the [GitHub CLI](https://cli.github.com/), logged in (`gh auth login`)
- [Claude Code](https://code.claude.com/docs). It runs `/memory-review`, the approval step.
- Optional: Claude.ai and/or ChatGPT

## 1. Create your private copy

On this project's GitHub page, click **Use this template → Create a new repository**, and set the visibility to **Private**.

> **Don't fork.** A fork of a public repository is public, and your memory would be too.

<details>
<summary>Command-line alternative</summary>

Download the template as a ZIP (**Code → Download ZIP**), unzip it, then inside the folder:

```bash
git init -b main && git add -A && git commit -m "Start from one-memory template"
```

```bash
gh repo create my-memory --private --source . --push
```

</details>

## 2. Clone it and point it at your repository

Replace `YOUR_USER/YOUR_MEMORY_REPO` with the repository you just created:

```bash
gh repo clone YOUR_USER/YOUR_MEMORY_REPO ~/my-memory
```

Then run these inside `~/my-memory`. The first creates the label that proposals use. The second replaces the `YOUR_USER/YOUR_MEMORY_REPO` placeholder in every file with your repository's real name (it works on macOS and Linux).

```bash
gh label create memory-proposal --color 5319E7 --description "Proposed change to memory"
```

```bash
REPO=$(gh repo view --json nameWithOwner --jq .nameWithOwner) && grep -rl --exclude-dir=.git 'YOUR_USER/YOUR_MEMORY_REPO' . | xargs perl -pi -e "s#YOUR_USER/YOUR_MEMORY_REPO#$REPO#g"
```

Look at the result with `git diff`, then save it:

```bash
git commit -am "Point one-memory at my repository" && git push
```

## 3. Connect Claude Code

Follow [platforms/claude-code.md](platforms/claude-code.md). It's one snippet in `~/.claude/CLAUDE.md`.

## 4. Fill in your memory

Follow [MAKE-IT-YOURS.md](MAKE-IT-YOURS.md). The quickest route is a short interview with Claude Code. You can also leave this for later: everything works with an empty memory, so you can test the plumbing first.

## 5. Connect your chat assistants (optional)

| Platform | Guide | What you get |
|---|---|---|
| Claude.ai | [platforms/claude-ai.md](platforms/claude-ai.md) | Read and propose (you approve each issue), or read-only |
| ChatGPT | [platforms/chatgpt.md](platforms/chatgpt.md) | Read; proposals by copy-paste unless your plan offers a connector that can create issues |

## 6. Verify

Instructions are not guarantees. Run the tests in [VERIFY.md](VERIFY.md) for every platform you connected. It takes about five minutes each.

## Afterwards

- When proposals arrive, run `/memory-review` in Claude Code inside `~/my-memory`.
- Your copy does not receive template updates automatically. To pick up improvements, compare it with the template and copy what you want. Your `memory/` folder is never touched.
