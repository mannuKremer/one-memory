# ChatGPT

| | How |
|---|---|
| Read | ChatGPT's GitHub app, when ChatGPT calls it (or uploaded project files) |
| Propose | Copy-paste fallback. Direct only if your account has a connector that can create issues |

_Last checked: November 2026. Plans and features change often. If a step doesn't match what you see, follow OpenAI's current help pages, then run [VERIFY.md](../VERIFY.md)._

## 1. Connect GitHub (read)

1. In ChatGPT, open Settings → **Apps** (formerly "Connectors") → **GitHub** → Connect.
2. On GitHub, install the ChatGPT app with **Only select repositories** and pick your memory repository.
3. Give it a few minutes. New repositories can take a while to show up.

Availability depends on your plan and on where you use it. Some accounts get GitHub in deep research or agent mode but not in regular chats. Test 1 tells you what you have.

**If the GitHub app isn't available in your chats:** create a ChatGPT Project and upload `PROTOCOL.md` and `memory/core.md` as project files. Re-upload them after each `/memory-review`.

## 2. Add instructions

Paste this into Settings → Personalization → **Custom instructions** (all chats), or into a Project's instructions (that Project only):

```text
My professional memory lives in my private GitHub repository YOUR_USER/YOUR_MEMORY_REPO and is the source of truth for professional facts about me. For work, code, career, learning or project topics, read memory/core.md there through the GitHub app and follow PROTOCOL.md from the same repository. If you can't read it, say "Memory not loaded." Never pretend. To remember something, follow PROTOCOL.md section 5. Never store health, family, financial, contact, ID, credential or confidential employer information.
```

## 3. Proposals

ChatGPT's GitHub app is documented as read-only. So, by default, ChatGPT uses the fallback in PROTOCOL.md: it prints the proposal in one code block, with a link to your issue form. Click the link, replace the example text with the block and submit. It takes about 15 seconds.

**Advanced (optional):** if your plan offers developer mode with MCP connectors, a connector that has an issue-creation tool lets ChatGPT open proposals itself, with a confirmation before each write. The setup differs by plan and changes often, so it isn't covered step by step here. If you set one up, limit it to your memory repository, keep write confirmations on, and run Tests 3 and 4 again.

## Limitations

- **Reading is not automatic.** ChatGPT decides when to use the GitHub app. The instructions make it likely, not certain. Saying "check my memory" helps. Run Test 1.
- ChatGPT's built-in memory keeps working separately and can contradict the repository. Once a professional fact lives here, consider removing it from ChatGPT's memory.
- Uploaded project files are snapshots.
