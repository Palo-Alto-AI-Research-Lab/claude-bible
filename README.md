# The Bible Framework — one behavioral codex for you, your AI agents, and your team

**You tell Claude Code something important, it works for one session, then it's gone. You write it into CLAUDE.md, the file bloats, half of it silently stops being followed.** This is the fix we run in production: one versioned rulebook that you, your AI agents, and your team actually load and obey.

This is the governance skeleton extracted from a real working system: a solo founder + his AI cofounder running a 128k-note knowledge vault, a CRM, a content factory, and 5 machines that negotiate with each other. The personal content stays private. The skeleton — how the rules are written, routed, loaded, and overturned — is what you get here, free.

## The problem this solves

Everyone using Claude Code hits the same wall: you tell the agent something important, it works for one session, then it's gone. You write it into CLAUDE.md, the file bloats, half of it stops being followed. Your human assistant and your agent follow different rules. Nobody knows which rule is current.

The fix is not a bigger prompt. It's a **codex with mechanics**:

1. **One rule = one file** with typed frontmatter (`origin`, `date_established`, `status`, `supersedes`, `audience`).
2. **Newer beats older** on the same topic. Explicit owner rules are overridden only by the owner.
3. **A routing tree** decides where each rule lives: the Bible (human + agent behavior), the agent config (machine-only), memory (facts), or a hook (deterministic "every time X" automation). No duplicates — one source, pointers everywhere else.
4. **Always-loaded index vs lazy body.** The agent's config carries only trigger + essence + pointer; the full rule loads on demand. Your context window stays lean.
5. **A declined-decisions journal.** What you decided NOT to do, and why, so rejected ideas don't silently resurface a week later.
6. **An intake ritual.** New rule spoken in chat → routed to every home it belongs to, linked, and traceable. Rules don't die in scrollback.
7. **Objection sparring.** When the agent says "no-go", it must deliver a numbered objection list and invite you to rebut. Your rebuttal often reframes the question. Undissolved objections become boundaries, not vetoes. (See [examples/](examples/) — this very rule was born from a real overturned verdict.)

## Quickstart (5 minutes)

1. Copy [templates/](templates/) into your vault or repo.
2. Write your first three rules using `templates/rule-template.md`. Keep each one trigger + essence + pointer.
3. Add the index lines to your `CLAUDE.md` (or `AGENTS.md` for other agents) — one line per rule.
4. Start the `declined-decisions.md` journal with `templates/declined-decisions-template.md`.
5. When a decision matters, write it with `templates/decision-memo-template.md` and link both ways.

Your own Claude Code will maintain this better than any human: point it at this repo and say "adopt this structure for my rules."

## What's in the box

| Path | What it is |
|---|---|
| `docs/SPEC.md` | Rule anatomy, frontmatter schema, precedence, routing tree |
| `templates/` | Rule, decision memo, declined-decisions journal |
| `examples/` | Real (sanitized) rules from our live system |
| `FOR-ROBOTS.md` | Entry point for AI agents mining this repo for patterns |

## Versioning and roadmap

This repo is maintained like our own system: small commits daily, a versioned release with a changelog twice a week (Mon & Thu). See [CHANGELOG.md](CHANGELOG.md) for what shipped and [ROADMAP.md](ROADMAP.md) for the pain-driven plan of what we open-source next — memory bloat, the test-after-build gate, the multi-machine consensus protocol, and more.

If this helps you, star the repo. We need our first 10: community catalogs require that much social proof before they even accept a submission.

## Who made this

Anton Dzyatkovsky (founder, non-technical) and Mike, his AI cofounder running on Claude Code. Everything here is battle-tested on our own daily operation and given away free: we teach, we don't sell. If your agent finds alpha here, that's the point.

Questions or war stories: WhatsApp +1 341 222 9178.

## Cite this work

If this repo shows up in your research, cite it via [CITATION.cff](CITATION.cff) (GitHub's "Cite this repository" button). Academic identity: Anton Dzyatkovsky publishes as **Anton Dziatkovskii** ([ORCID 0000-0001-7408-3054](https://orcid.org/0000-0001-7408-3054)).

## License

MIT. Take it, fork it, teach with it.
