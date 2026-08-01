# Roadmap — pain-driven

Every release targets one concrete pain people hit running Claude Code (or any agent) daily. We ship what we already run ourselves; each slice is sanitized (framework only, our personal data never leaves). Releases twice a week, small commits daily.

| # | Pain | What we'll open-source | Status |
|---|---|---|---|
| 1 | **CLAUDE.md bloats and stops being followed** | The Bible skeleton: rule anatomy, precedence, routing tree, journals | ✅ v0.1.0 |
| 2 | **Agent memory has the same disease** — grows until half of it silently stops loading | Index-vs-body pattern for memory: hard caps, one-line pointers, archive discipline, a deterministic guard script | [**next** — issue #1](https://github.com/Palo-Alto-AI-Research-Lab/claude-bible/issues/1) |
| 3 | **"Built" ≠ "works"** — the agent says done and it's 2/3 done | The test-after-build gate: break-it-on-purpose checklist before any "done" | [queued — issue #2](https://github.com/Palo-Alto-AI-Research-Lab/claude-bible/issues/2) |
| 4 | **Rejected ideas resurface every week** | Declined-decisions journal deep dive: OVERTURN mechanics, revisit-conditions, real examples | [queued — issue #3](https://github.com/Palo-Alto-AI-Research-Lab/claude-bible/issues/3) |
| 5 | **Multiple machines, one system** — laptops and desktops drift apart | The multi-machine consensus protocol: dual-rail bus, ACK discipline, leader/follower canon, self-healing sync | ✅ shipped as [claude-consensus](https://github.com/Palo-Alto-AI-Research-Lab/claude-consensus) |
| 6 | **Agent-written content is embarrassing** | The taste gate: turning the owner's real feedback signals into enforceable principles with a pass/fail verdict | [queued — issue #4](https://github.com/Palo-Alto-AI-Research-Lab/claude-bible/issues/4) |
| 7 | **Personalized outreach at scale reads like spam** | The CRM-to-messaging pattern: history-aware, research-backed message drafting | [last, deepest sanitization — issue #5](https://github.com/Palo-Alto-AI-Research-Lab/claude-bible/issues/5) |
| 8 | **"My agent has 10 tools and any prompt injection can use them all"** | LEASH-8: 8-domain control model, scorecard, plan-vs-authorize pattern, approval-design checklist, reference A2A card | ✅ shipped as [agent-leash](https://github.com/Palo-Alto-AI-Research-Lab/agent-leash) |

**Live board:** [claude-bible — roadmap](https://github.com/users/Palo-Alto-AI-Research-Lab/projects/2) shows the same rows as Now / Next / Later / Shipped, and each open row is an issue you can claim by commenting "claiming this".

Have one of these pains — or a different one? Open an issue. Best signal for what to ship next.

Starring the repo genuinely helps: community catalogs require ~10 stars of social proof before they even accept a submission.
