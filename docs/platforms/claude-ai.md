# Claude.ai

There are two ways to connect. Option A lets Claude open proposals for you. Option B is simpler, but read-only.

| | Read | Propose |
|---|---|---|
| A. GitHub connector | When Claude calls the connector | Claude opens the issue, after you approve |
| B. Project knowledge | Files you add to a Project (a snapshot) | Copy-paste fallback |

_Last checked: November 2026. Claude's settings change. If a step doesn't match what you see, follow Anthropic's current help pages, then run [VERIFY.md](../VERIFY.md)._

## Option A: GitHub connector (read and propose)

Claude connects to GitHub's hosted MCP server. Access to private repositories goes through Anthropic's GitHub App for this connector, which you limit to your memory repository.

1. **Add the connector.** In Claude, open Settings → Connectors → **Add custom connector**.
   - URL: `https://api.githubcopilot.com/mcp/`
   - Sign in with GitHub when asked.

   On Team and Enterprise plans, an owner adds custom connectors. Free plans allow one custom connector.
2. **Limit access to your memory repository.** Install the GitHub App [claude-github-mcp-connector](https://github.com/apps/claude-github-mcp-connector), and check that its developer is **anthropics**. Choose **Only select repositories** and pick your memory repository.
   Without this step, sign-in succeeds but your private repository looks like it doesn't exist ("not found").
3. **Set tool permissions** on the connector's settings page:
   - Read tools (file contents, listing and searching issues): allow.
   - The issue-writing tool: **needs approval**. It can also edit and close issues, which is why you approve every call.
   - Everything else that writes (pull requests, files, branches): **blocked**.
4. **Add the instructions** from the block below.
5. **Turn it on in chats.** If the connector's tools don't appear in a conversation, enable it from the chat's tools menu.

## Option B: Project knowledge (read-only)

1. Create a Project, for example "Work".
2. In project knowledge, click **+ → GitHub**, pick your memory repository, and select `PROTOCOL.md` and the `memory/` folder.
3. Paste the instruction block into the Project instructions.
4. After each `/memory-review`, click **Sync** in project knowledge. Otherwise Claude keeps reading the old snapshot.

Proposals use the copy-paste fallback from PROTOCOL.md: Claude prints the proposal and a link, and you paste it into the issue form.

## Instruction block

Paste it into Settings → Profile → **personal preferences** (all chats), or into a Project's **instructions** (that Project only):

```text
My professional memory lives in my private GitHub repository YOUR_USER/YOUR_MEMORY_REPO. It is the source of truth for professional facts about me.
In conversations about work, code, career, learning or my projects:
- Read memory/core.md from that repository first, and follow PROTOCOL.md from the same repository.
- If you can't read it, say "Memory not loaded." in one line. Never pretend you read it.
- To remember something, propose it exactly as PROTOCOL.md section 5 describes. Never edit repository files.
- Never store health, family, financial, contact, ID, credential or confidential employer information.
```

## Limitations

- **Reading is not automatic.** Claude decides when to call the connector. The instructions make it likely, not certain. If an answer seems to ignore your memory, say "check my memory". Test 1 shows how reliable it is for you.
- The GitHub App's own permissions are broader than this needs. Limiting it to one repository confines them to that repository, and the tool permissions above keep Claude to reading and opening issues.
- Project knowledge (Option B) is a snapshot that needs a manual sync.
