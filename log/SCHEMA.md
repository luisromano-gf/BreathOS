# Log Schema

**Version:** 0.1  
**Datestamp:** 2026-03-27

---

## Purpose

The log is not a diary. It is the organism's episodic memory.

It must capture not just *what* was decided, but *why*, what the alternatives were, and what would cause revisiting it. Without this, the system cannot distinguish evolution from drift.

---

## Entry types

| Type | Purpose | Filename pattern |
|------|---------|-----------------|
| `origin` | System birth, major resets | `000-origin.md` |
| `decision` | A choice made and why | `YYYY-MM-DD-decision-[slug].md` |
| `delta` | Something in the map changed | `YYYY-MM-DD-delta-[cluster].md` |
| `reflection` | Periodic self-assessment | `YYYY-MM-DD-reflection.md` |
| `failure` | Something broke, what we learned | `YYYY-MM-DD-failure-[slug].md` |

---

## Decision entry schema

```markdown
# Decision: [title]

**Date:** YYYY-MM-DD
**Type:** decision
**Domain:** compass | map | engine | hardware | stack | other
**Status:** active | superseded | archived

## Context
What was the situation? What prompted this decision?

## Options considered
1. Option A — [brief description, tradeoffs]
2. Option B — [brief description, tradeoffs]
3. Option C — [brief description, tradeoffs]

## Decision made
[What was chosen and the core reasoning]

## Why not the others
[Honest account of what was set aside and why]

## Trigger for revisiting
[The specific signal that would cause re-evaluating this decision]
Example: "When a 70B model runs at >20 tok/s on my hardware with 4-bit quant"
Example: "When open-weight models score >90% on MMLU reasoning benchmarks"

## Outcome (fill in later)
[Left blank at decision time. Updated when outcome is known.]
```

---

## Delta entry schema

```markdown
# Delta: [cluster name]

**Date:** YYYY-MM-DD
**Type:** delta
**Cluster:** architectures | models | intelligence | memory | modalities | deployment | hardware | impact
**Triggered by:** [what signal caused this update]

## What changed
[Specific facts that are now different from the previous map state]

## Previous state
[What the map said before — quote or reference the old entry]

## Updated state
[What the map says now]

## Impact on decisions
[Does this delta invalidate any active decisions in the log? List them.]

## Sources
- [URL or reference, with date accessed]
```

---

## Principles for logging

- **Log before fixing.** When something fails, document it first.
- **Be specific about triggers.** "When things change" is not a trigger. "When X metric crosses Y threshold" is.
- **Outcomes are filled in later.** A decision log without outcomes is incomplete. Come back.
- **Every delta traces to a source.** No undated, unsourced updates.
- **Superseded entries are never deleted.** Mark as `superseded`, link to what replaced them.
