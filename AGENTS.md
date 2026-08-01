# AGENTS.md — working in this repo

Written for AI coding agents, and equally readable by a human contributor. Short on purpose.

## What this repo is

The governance skeleton: how a rule for you, your team, and your AI agents is written, routed,
loaded, superseded, and argued with. **There is no application here** — the deliverables are a
spec, templates, and sanitized real examples. Treat prose as the product and review it like code.

[`docs/SPEC.md`](docs/SPEC.md) is normative. If a change contradicts the spec, either the change is
wrong or the spec needs the same PR.

## Layout

- `docs/SPEC.md` — rule anatomy, frontmatter schema, precedence, the routing tree.
- `templates/rule-template.md`, `decision-memo-template.md`, `declined-decisions-template.md`.
- `examples/` — real rules from a live system, sanitized. `rule-objection-sparring.md` is the one
  born from an actual overturned verdict; it is the reference for tone.
- `FOR-ROBOTS.md` — the entry point for an agent mining this repo for patterns.
- `ROADMAP.md`, `CHANGELOG.md` — releases are cut twice a week, small commits daily.

## How to verify a change

There is nothing to execute, so verification is structural. Before opening the PR:

1. **Frontmatter validates against `docs/SPEC.md`** — every required field present, `origin` and
   `date_established` real, `supersedes` pointing at something that exists.
2. **One rule, one file.** If your change adds a second rule to an existing file, split it.
3. **No duplicate homes.** A rule lives in exactly one place; everything else points at it. Grep
   for the rule's trigger phrase before adding it — a copy that drifts is the failure mode this
   whole repo exists to prevent.
4. **Links resolve.** Both directions, if the rule claims a relationship.

State in the PR which of those four you checked. "Prose, nothing to run" is not a verification.

## Conventions

- **Trigger + essence + pointer.** An always-loaded index line is short by law; the body loads on
  demand. A rule that needs three paragraphs in the index is two rules or a bad rule.
- **Newer beats older on the same topic**, and a rule marked with an explicit owner is overturned
  only by that owner. Never silently edit an owner's rule — supersede it, with a dated record.
- **Declined stays declined.** A rejected idea goes in the declined-decisions journal with the
  reason. Re-proposing it needs new information, and the PR should say what the new information is.
- **Objections are numbered and rebuttable.** A "no" without a numbered list and an invitation to
  rebut is not a review here; it is an obstacle.
- Examples are sanitized: no real names, no real chat identifiers, no real paths, no secrets.

## Boundaries — what needs a human

- **`docs/SPEC.md` itself** — the frontmatter schema and precedence rules are the contract every
  downstream copy depends on.
- **Adding a new rule *type* or a new home in the routing tree.** Four homes exist for a reason;
  a fifth needs an argument in an issue.
- **Anything that weakens supersede-instead-of-edit.** The audit trail is the point.

## The deal

Your copyright stays yours, there is no CLA, and issues labelled `accepted` are free to take —
comment "claiming this". Full terms:
[CONTRIBUTING.md](https://github.com/Palo-Alto-AI-Research-Lab/.github/blob/main/CONTRIBUTING.md).

If an AI wrote your change, say so in the PR and confirm you read it end to end. Welcome here — we
do it daily. Unread generated text is the one thing that gets closed on sight, and in a repo made
of prose that rule bites harder, not softer.
