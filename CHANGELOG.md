# Changelog

All notable changes to this project. Small commits land daily as work happens; **every noticeable
change ships as a release**, so the release feed is the record of maturity. (The line here used to
promise a release twice a week — between 4 July and 4 August 2026 not one was cut, so the promise
was replaced with a rule tied to the work instead of the calendar.) Format: what shipped, in plain words.

## v0.1.5 — 2026-08-29

Two mechanics the spec was missing, both about the gap between a rule being *written* and a rule
being *run*. Both come from measurements on our own codex.

- **§9 One rule = one door.** A rule with no caller is accepted, filed, linked and never fires.
  A door is something that invokes — a skill, a command, a scheduled job, a hook; the codex and
  the agent config are read, not called, so neither is a door. Measured 2026-08: 19 of 25 recent
  rules had none (76%), and one sat 42 days without a single application. Names the two shapes:
  *no door*, and the worse *fictitious door* — the rule's name sitting in a skill as prose with
  no command beside it, which answers "is it wired?" with a false yes.
- **§10 Writing the rule is never gated by the file's size.** Accepting a rule and compacting the
  always-loaded index are different jobs with different owners. The session that hears a rule
  writes it, red zone or not, and reports the size in one line; compaction is a separate daily
  job. A size check in front of an intake is a measurement for the report, not a brake.
- README lists both; the docs site headline now says nine mechanics, not seven.
- Docs page housekeeping: 20 links on `docs/index.html` still pointed at the pre-rename
  org. They **do** still resolve — GitHub serves the redirect, measured 2026-08-29 — so
  this is tidiness, not a repair: the published page now names the current owner directly
  instead of relying on a redirect staying alive.

## v0.1.4 — 2026-08-25

Three docs commits, all housekeeping after the account rename to `tonydzi`: dead github.io links
fixed across the repo, a contact footer with the engineer CTA on the README, and two pieces now
pointing at the system map instead of describing the system ad hoc. No rule text changed. Cut by
the first run of the weekly release pass — the routine v0.1.3 asked for. Written into this file
on 2026-08-29; the release was cut on 25 Aug and the changelog was not updated with it.

## v0.1.3 — 2026-08-04

The repo became something a stranger can contribute to, and the versions caught up with reality:
v0.1.2 was written on 2026-07-04 and never tagged, so its tag and this one were both cut on
2026-08-04. Nothing was backdated.

- **Docs site** at [/docs](https://tonydzi.github.io/claude-bible/), linked from the README.
- **`AGENTS.md`** — how to verify a change when there is nothing to execute: four structural checks, because "it's prose, there's nothing to run" is not a verification story.
- **Every open roadmap row is now a claimable issue** — `accepted` means scoped, free to take, nobody on it. Comment "claiming this" and it is yours for 7 days.
- **The contributor deal in the open**: no CLA, you keep your copyright, an answer within 48 hours including "no, and here is why". Inherited from one org-wide `CONTRIBUTING.md` rather than a local copy that silently shadows it.
- `CITATION.cff`, `SUPPORT.md`, the lab-wide AI-contributor credit policy, and changelog categories for auto-generated release notes.

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
