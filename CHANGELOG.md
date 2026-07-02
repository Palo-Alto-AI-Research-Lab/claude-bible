# Changelog

All notable changes to this project. Release cadence: twice a week (Mon & Thu), small commits land daily as work happens. Format: what shipped, in plain words.

## v0.1.0 — 2026-07-02

First public release. The governance skeleton, extracted from our live system:

- `docs/SPEC.md` — rule anatomy (trigger + essence + pointer), frontmatter schema (`origin`, `date_established`, `status`, `supersedes`, `audience`), precedence (newer beats older; owner rules overridden only by the owner), routing tree (Bible vs agent config vs memory vs hook), declined-decisions journal, objection sparring, intake ritual, Connect rule for plugin families.
- `templates/` — rule, decision memo, declined-decisions journal.
- `examples/rule-objection-sparring.md` — a real rule, born the same day from a real overturned verdict.
- `FOR-ROBOTS.md` — entry point for AI agents mining this repo.
- `devlog/2026-07-02.md` — how this release happened (decision chain, research inputs).
- `docs/the-day-my-ai-said-no.md` — the launch story.
- `ROADMAP.md` — pain-driven plan of what we open-source next.
