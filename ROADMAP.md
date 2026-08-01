# Roadmap — pain-driven

Every release targets one concrete pain people hit running Claude Code (or any agent) daily. We ship what we already run ourselves; each slice is sanitized (framework only, our personal data never leaves). Releases twice a week, small commits daily.

| # | Pain | What we'll open-source | Status |
|---|---|---|---|
| 1 | **CLAUDE.md bloats and stops being followed** | The Bible skeleton: rule anatomy, precedence, routing tree, journals | ✅ v0.1.0 |
| 2 | **Agent memory has the same disease** — grows until half of it silently stops loading | Index-vs-body pattern for memory: hard caps, one-line pointers, archive discipline, a deterministic guard script | next |
| 3 | **"Built" ≠ "works"** — the agent says done and it's 2/3 done | The test-after-build gate: break-it-on-purpose checklist before any "done" | queued |
| 4 | **Rejected ideas resurface every week** | Declined-decisions journal deep dive: OVERTURN mechanics, revisit-conditions, real examples | queued |
| 5 | **Multiple machines, one system** — laptops and desktops drift apart | The multi-machine consensus protocol: dual-rail bus, ACK discipline, leader/follower canon, self-healing sync | ✅ shipped as [claude-consensus](https://github.com/Palo-Alto-AI-Research-Lab/claude-consensus) |
| 6 | **Agent-written content is embarrassing** | The taste gate: turning the owner's real feedback signals into enforceable principles with a pass/fail verdict | ✅ shipped |
| 7 | **Personalized outreach at scale reads like spam** | The CRM-to-messaging pattern: history-aware, research-backed message drafting | last (deepest sanitization) |
| 8 | **"My agent has 10 tools and any prompt injection can use them all"** | LEASH-8: 8-domain control model, scorecard, plan-vs-authorize pattern, approval-design checklist, reference A2A card | ✅ shipped as [agent-leash](https://github.com/Palo-Alto-AI-Research-Lab/agent-leash) |

Have one of these pains — or a different one? Open an issue. Best signal for what to ship next.

Starring the repo genuinely helps: community catalogs require ~10 stars of social proof before they even accept a submission.

---

## Row 6 — The taste gate

### The pain

Agent-written content is embarrassing in a way that is hard to name and easy to recognise: the even rhythm, the "not just X, but Y", the summary of the summary, the enthusiasm nobody asked for. "Make it better" is not an instruction a model can act on twice the same way.

### Method: deriving principles from a feedback corpus without inventing taste

The core discipline is **never invent a principle**. Every rule must trace back to an actual correction a human made on a real draft.

**Step 1 — collect raw corrections, not opinions**

Gather every edit a human made to agent output: tracked-changes documents, inline comments, Slack reactions that prompted a rewrite, email replies that said "no, try again". The corpus is corrections, not style advice written after the fact. Style advice written after the fact describes an imagined ideal; corrections describe a real failure.

**Step 2 — cluster by failure mode, not by topic**

Group corrections by what went wrong structurally, not by subject matter. Recurring clusters become candidate principles. A candidate principle requires at least three independent corrections in its cluster before it is admitted; one correction is an accident, two is a pattern beginning, three is a rule.

**Step 3 — write each principle as a falsifiable claim with a counter-example**

A principle is not a preference ("be concise"). It is a testable claim with a named failure mode and a counter-example that a judge can use:

```
Principle: No "not just X, but Y" constructions.
Failure mode: paired contrast used for emphasis where the second clause
              restates the first rather than adding information.
Counter-example (FAIL): "This is not just a tool, but a system."
Counter-example (PASS): "This handles retries; it does not handle timeouts."
```

**Step 4 — assign each principle to a detector tier**

Two tiers only:

- **Deterministic** — a regex or length measurement can decide pass/fail with zero false negatives on the training corpus. Use this tier first.
- **LLM judge** — only for what a regex genuinely cannot see. The judge receives the principle, the counter-examples, and the span under scrutiny. It returns pass/fail plus the offending span quoted verbatim. No summary, no score, no explanation longer than one sentence.

The split matters because a deterministic detector is auditable. When a writer disputes a failure, you can show the exact match. An LLM judge cannot be audited the same way; its scope must be narrow enough that a reasonable person would agree with it nine times out of ten.

---

### Worked gate: the markers and the measurements that justify them

The following principles were derived from a real correction corpus. Each marker shows the measurement used to set the threshold.

---

#### Marker 1 — Banned constructions (deterministic)

**Principle:** The following constructions are banned unconditionally.

| Construction | Pattern | Why it was banned |
|---|---|---|
| `not just X, but Y` | `/not just .{3,60}, but /i` | Appeared in 11 of 14 rejected drafts. Signals performed emphasis. |
| `in conclusion` / `to summarize` | `/\b(in conclusion|to summarize|in summary)\b/i` | Every instance was a restatement of content already present. |
| `it is worth noting` | `/it is worth noting/i` | Hedge that adds no information. All 7 instances were deleted without replacement. |
| `at the end of the day` | `/at the end of the day/i` | Present in zero accepted drafts. |
| Exclamation marks in body text | `/[^!]![^!]/` | Removed in 100% of edits where present. Allowed only in direct quotation. |

**Measurement:** Each pattern was run against the accepted-draft corpus and the rejected-draft corpus. A pattern is admitted to the banned list only if its rejected-draft frequency is at least 4× its accepted-draft frequency.

**Verdict:** Any match → FAIL. Quote the matching span.

---

#### Marker 2 — Sentence-length variance (deterministic)

**Principle:** A passage of five or more consecutive sentences must not have a coefficient of variation (CV) of sentence length below 0.4.

**Why:** Even rhythm is the single most consistent signal of agent-generated text. A CV below 0.4 means sentences are too uniform in length. Human prose varies. This is not a style preference; it is a measurable structural property.

**Measurement:**

```
CV = std(sentence_lengths) / mean(sentence_lengths)

Accepted-draft corpus (n=47 passages of 5+ sentences):
  median CV = 0.61, 10th percentile = 0.42

Rejected-draft corpus (n=38 passages of 5+ sentences):
  median CV = 0.31, 90th percentile = 0.39

Threshold set at 0.4: catches 89% of rejected passages,
flags 8% of accepted passages (acceptable false-positive rate
given that the rewrite cost is low).
```

**Verdict:** CV < 0.4 on any five-sentence window → FAIL. Report the window and its CV.

---

#### Marker 3 — Summary-of-summary (deterministic + LLM judge)

**Principle:** A document may not end with a paragraph that restates claims already made in the document body.

**Deterministic pre-filter:** Flag any final paragraph that begins with a banned restatement opener:

```
/^(In (summary|conclusion|short|brief)|To (summarize|recap|conclude)|
   (All|Taken) together|Putting (this|it) (all )?together)/im
```

**LLM judge (for passages that pass the pre-filter):** The judge receives:

```
PRINCIPLE: The final paragraph must not restate claims already present
           in the document body.

COUNTER-EXAMPLE (FAIL):
  Body contains: "The system cuts latency by 40%."
  Final paragraph contains: "As we have seen, latency is reduced."

COUNTER-EXAMPLE (PASS):
  Final paragraph introduces next action or open question
  not addressed in the body.

PASSAGE TO JUDGE:
  [body]
  [final paragraph]

Return: PASS or FAIL. If FAIL, quote the offending sentence.
```

**Verdict:** Pre-filter match or LLM judge FAIL → FAIL.

---

#### Marker 4 — Length relative to information (LLM judge only)

**Principle:** The document must not contain more words than the information density warrants. Concretely: the LLM judge must be unable to remove a sentence without losing a claim, a number, or a named entity.

This principle cannot be measured with a regex. A document that contains only one sentence per claim is not automatically short enough; a document with three sentences per claim is not automatically too long if each sentence adds a distinct piece of information.

**LLM judge prompt:**

```
PRINCIPLE: Every sentence must add a claim, a number, or a named entity
           not present in any earlier sentence.

TASK: Read the following document sentence by sentence. For each sentence,
      determine whether removing it would cause a reader to lose information.
      List every sentence where the answer is NO.

DOCUMENT:
  [document]

Return: PASS if the list is empty. FAIL if the list is non-empty.
If FAIL, quote each sentence that could be removed without loss.
```

**Verdict:** Any removable sentence identified → FAIL.

---

### Running the gate

```
taste-gate <file>

Exit codes:
  0  PASS — no markers triggered
  1  FAIL — one or more markers triggered; offending spans printed to stdout
  2  ERROR — file could not be read or LLM judge unavailable

Output format (on FAIL):
  FAIL  marker-2  CV=0.31  span="We built the system carefully. We tested it
        thoroughly. We shipped it on time.