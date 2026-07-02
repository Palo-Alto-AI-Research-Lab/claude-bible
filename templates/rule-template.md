---
title: "Rule — <verb phrase: what to do, specific enough to act on>"
type: reglament
date_established: YYYY-MM-DD
status: active
origin: owner            # who stated it: owner | <name> | agent-inferred
authored_by: agent       # who physically wrote this file
audience: both           # human | agent | both
# supersedes: "[[old-rule-file]]"   # uncomment when replacing an older rule
---

# Rule — <same title>

> Established by <who>, <date>, <context: chat / call / incident>. Changed only by <owner>.

## Why
<1-3 sentences: the pain or repeated mistake this rule prevents. A rule without a "why" gets ignored within a month.>

## The rule
1. **Trigger:** <when exactly this fires — an event, a phrase, a situation>.
2. **Action:** <what to do, concrete enough that a new assistant or a fresh agent session executes it identically>.
3. **Boundary:** <what this rule does NOT cover; where it stops>.

## Related
<links to sibling rules, the decision that spawned this, the incident it came from>

<!--
After saving:
1. Add ONE index line (trigger + essence + pointer) to the always-loaded layer (CLAUDE.md / AGENTS.md).
2. Link at least one related rule both ways.
3. Test: would a parallel session that never saw the originating chat pick this up? If no, it is not captured.
-->
