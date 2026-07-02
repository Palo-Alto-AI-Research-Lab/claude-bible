# SPEC — how the Bible works

## 1. Rule anatomy

A rule is one markdown file. Body = full canon. The always-loaded layer (CLAUDE.md / AGENTS.md / MEMORY index) carries only a compressed line: **trigger + essence + pointer**.

```
## <Trigger — when this fires>
<Essence in 1-3 sentences: what to do / not do, and why it exists.>
Canon: `<rule-file-name>` (+ related rules as links).
```

Why: the full text of every rule in the system prompt = bloat and decay. The index line fires recognition; the body loads on demand.

## 2. Frontmatter schema

```yaml
---
title: "Rule — <verb phrase, specific>"
type: reglament          # reglament | protocol | decision | concept
date_established: 2026-07-02
status: active           # active | superseded | deferred
origin: owner            # owner = the human principal; or the actual author
authored_by: agent       # who physically wrote the file
audience: both           # human | agent | both
supersedes: "[[old-rule]]"   # optional
---
```

- `origin: owner` marks rules stated by the principal. **Only the owner overrides them** (or an explicit `supersedes` from a newer owner rule).
- `date_established` resolves conflicts: **newer beats older on the same topic**.
- `audience` lets one codex serve humans and agents: a human assistant and a Claude session read the same rule.

## 3. Precedence

1. Newer beats older (same topic).
2. `origin: owner` beats agent-inferred rules regardless of date.
3. Explicit `supersedes` beats both — but keep the old file, mark it `status: superseded`, and link forward. History is data.
4. An overturned verdict gets an **OVERTURN** mark in the declined-decisions journal so no parallel session cites the dead version as live.

## 4. Routing tree — where does a new rule live?

Ask in order:

1. **Could a human employee execute it?** → it goes in the Bible (behavioral codex). The agent layer references it, never duplicates it.
2. **Is it about how the agent works internally** (model choice, tool habits, file paths)? → agent config (CLAUDE.md / AGENTS.md) + a memory file.
3. **Is it a fact or preference**, not a behavior? → memory.
4. **Is it "every time X happens, do Y" and deterministic?** → a hook or scheduled script, not prose. Prose rules decay; hooks fire.

One home per rule. Every other layer points to it.

## 5. The declined-decisions journal

Memory stores what is true NOW. This journal stores what you decided **NOT** to do and why — the half that plain memory lacks. Before proposing anything structural, the agent scans it. A declined item reopens only when its recorded `Revisit if` condition holds, or explicitly as a trade-off quoting the original decline. Never as a fresh amnesiac idea.

## 6. Objection sparring (verdicts are not sentences)

When the agent concludes "don't do it / not yet / no-go" on something the principal wants:

1. Deliver the verdict as a **numbered list of objections** — one real objection per line, not buried in prose.
2. Explicitly invite rebuttal: "here are my objections — convince me."
3. Treat the rebuttal as data. It often changes the **frame**, not the arguments (our origin case: "paid product" reframed to "free school" dissolved 14 objections in one pass).
4. Synthesize: a table of objection → dissolved (why) / stands. What stands becomes a **boundary inside the new decision**, not a veto.
5. Anti-sycophancy: dissolution must be argued. If a rebuttal didn't close an objection, say so plainly. Consensus = honest deadlock of mutual persuasion, not capitulation.
6. Symmetric: when the principal rejects the agent's idea, the agent may request objections as a list and work them — respecting the declined journal.

## 7. The intake ritual

A new rule spoken in chat is not "noted" — it is **routed**: written to its home (tree above), linked to related rules, given a trace in the always-loaded layer, and reported back ("rule lives here, index line added there"). Test before saying done: will a parallel session that never saw this chat pick the rule up by itself? If no, it isn't captured.

## 8. Skill/plugin family pattern (Connect rule)

When you split a system into plugins, each plugin declares its family and its handoffs: what it takes in, what it passes on, and to whom. The sender owns the RESULT, not the delivery — "passed it along" is not "done", silence is not success. A pipeline is finished when the receiving end confirms.
