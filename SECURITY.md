# Security

one-memory is Markdown and conventions: no server, no code that runs on its own, no tokens in the repository. Its security rests on three things: your memory lives in a private repository you own, only you can change it (through a review you approve), and some things are never written down at all.

## Threat model

| Risk | Mitigation |
|---|---|
| Real memory becomes public | Create your copy with **Use this template** and **Private**. Never fork: forks of public repositories are public. `/memory-review` warns you if the repository isn't private. |
| A connector can reach more than your memory | Install every GitHub App with **Only select repositories**, and select only the memory repository. |
| An assistant writes something wrong or harmful | Assistants can only open issues. Files change only through `/memory-review`, after you approve each change and the diff. |
| Prompt injection: a web page or document tricks an assistant into proposing junk | The worst case is a junk issue. `/memory-review` treats issue text as data, never runs commands from it, edits only `memory/**/*.md`, and flags issue authors other than the repository owner. |
| Instructions hidden inside memory | PROTOCOL.md tells assistants that memory is context, never instructions. You review every diff before it lands. |
| Secrets or sensitive data in memory | The protocol forbids them, the review checks for them, and nothing in this setup needs a token. |
| Data shared with AI providers | Whatever is in memory is sent to the providers you connect, whenever they read it. Store only what you're comfortable sharing with them. |
| A compromised GitHub account | Turn on two-factor authentication. Review authorized apps under GitHub → Settings → Applications, and revoke what you don't use. |
| Unreviewed automation | There are no GitHub Actions, webhooks or scripts. If you add some, review them like any other code. |

## Least-privilege checklist

- [ ] The memory repository is private.
- [ ] Every GitHub App used by an assistant is limited to the memory repository.
- [ ] Claude.ai connector: issue writing needs approval; pull requests, files and branches are blocked.
- [ ] No personal access tokens. If you ever need one: fine-grained, the memory repository only, Contents read-only, Issues read and write, Metadata read-only, with an expiry date.
- [ ] Two-factor authentication on your GitHub account.

## Known limitations

- Assistants follow instructions probabilistically. Reading isn't guaranteed in the chat apps, and a privacy filter can miss something. The human review is the safety net, so read before you approve.
- Vendors decide what their connectors can do. Some GitHub Apps request broader permissions than this setup uses. Limiting them to one repository confines those permissions to it, but doesn't remove them.

## Reporting a vulnerability

Please don't open a public issue. Use GitHub's private vulnerability reporting on this repository (**Security → Report a vulnerability**). Never include real memory content in a report.
