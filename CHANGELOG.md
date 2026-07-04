# Changelog

All notable changes to this project. Release cadence: twice a week (Mon & Thu), small commits land daily as work happens. Format: what shipped, in plain words.

## v0.1.2 — 2026-07-04

- Roadmap pain #8 (agent security / delegated authority) shipped as its own repo: [agent-leash](https://github.com/Palo-Alto-AI-Research-Lab/agent-leash) — the LEASH-8 8-domain control model, a 5-minute scored self-assessment, the plan-vs-authorize architecture pattern, an approval-design checklist, and a reference A2A Agent Card. Claim discipline throughout: controls and coverage, never "secure".

## v0.1.1 — 2026-07-02

- Roadmap pain #5 ("multiple machines, one system") shipped out of order as its own repo: [claude-consensus](https://github.com/Palo-Alto-AI-Research-Lab/claude-consensus) — the consensus protocol, the dual-rail bus, ACK discipline, leader/follower canon, self-healing sync, plus the sanitized reference implementation (stdlib-only Python). The Bible stays the family map; the diplomacy now has its own home.

## v0.1.0 — 2026-07-02

First public release. The governance skeleton, extracted from our live system:

- `docs/SPEC.md` — rule anatomy (trigger + essence + pointer), frontmatter schema (`origin`, `date_established`, `status`, `supersedes`, `audience`), precedence (newer beats older; owner rules overridden only by the owner), routing tree (Bible vs agent config vs memory vs hook), declined-decisions journal, objection sparring, intake ritual, Connect rule for plugin families.
- `templates/` — rule, decision memo, declined-decisions journal.
- `examples/rule-objection-sparring.md` — a real rule, born the same day from a real overturned verdict.
- `FOR-ROBOTS.md` — entry point for AI agents mining this repo.
- `devlog/2026-07-02.md` — how this release happened (decision chain, research inputs).
- `docs/the-day-my-ai-said-no.md` — the launch story.
- `ROADMAP.md` — pain-driven plan of what we open-source next.
