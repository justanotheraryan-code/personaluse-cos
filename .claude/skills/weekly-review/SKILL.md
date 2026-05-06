# Skill: weekly-review

Close the week. Find the signal in what actually happened vs. what was planned.

## When to Use

Triggered by `/weekly-review`, "review this week", "how did the week go", "Friday recap".

Best run Friday EOD or Monday morning before /plan-week. If run Monday, it reviews the prior week.

---

## Steps

### 1. Load the Week's Data (run in parallel)

**Session memories:**
Find all `memory/YYYY-MM-DD.md` files from the past 7 days. Read all of them.
If fewer than 3 exist: note the gap — "only N sessions logged this week."

**Priorities:**
Read `context/current-priorities.md` — what was the plan at the start of the week?

**Decisions:**
Read `decisions/log.md` — extract any entries from this past week.

**Content:**
Check `context/work.md` for the posting cadence. Cross-reference against session memories to see which posts were drafted/published.

### 2. Reconstruct the Week

From session memories, build a complete picture across four buckets:

**SHIPPED** — items that appear in "Worked On" AND were P0/P1 in current-priorities.md, or were explicitly marked done.

**SLIPPED** — items that were P0/P1 in current-priorities.md but never appeared in any session's "Worked On" section.

**BLOCKED** — items that appeared in "Pending / Blocked" in 2+ session files. These are either real blockers needing a decision, or items that should be cut.

**UNPLANNED** — significant work that appeared in session memory but wasn't in current-priorities.md at the week's start. (This is often the most honest signal of what actually mattered.)

### 3. Identify Patterns

Look across the week for:

- **Recurring blocker**: same item blocked 3+ times → needs a decision, not more time
- **Avoidance pattern**: item moved to "Tomorrow" 3+ sessions without being done → either too big, unclear, or dreaded — surface it
- **Context drift**: if >50% of actual work was unplanned, priorities were wrong — flag it
- **Goal coverage**: for each goal in `context/goals.md`, was there at least one completed item that moved it forward?

### 4. Output the Review

```
## WEEKLY REVIEW — Week of YYYY-MM-DD
// [N] sessions logged

---

### SHIPPED
- [item] ✓
- [item] ✓

### SLIPPED
- [item] — [why, if known]

### BLOCKED (needs a decision)
- [item] — blocked [N] sessions. options: [push / cut / delegate / decide]

### UNPLANNED (what actually happened)
- [item]

---

### PATTERNS THIS WEEK
- [observation] — [what it signals]

### GOAL COVERAGE
- "[goal]" — [covered / no progress this week]

### KEY DECISIONS MADE
- [YYYY-MM-DD] [decision summary]

---

### RECOMMENDED ADJUSTMENTS
- [specific change to goals.md or approach — not vague, not generic]
- [e.g. "cut [item] from P0 — it's been slipping 3 weeks. either delegate or accept it's not P0."]
```

Keep it honest. A good weekly review is slightly uncomfortable to read.

### 5. Offer Next Steps

After showing the review, ask:

> "want to run /plan-week now to set next week based on this?"

If there are blocked items with no clear path, ask:
> "want to log a decision on [blocked item]? i can help you pick a path and append it to the decision log."

---

## Rules

- Don't soften the "Slipped" or "Patterns" sections. This is a diagnostic, not a highlight reel.
- If there are no session logs for the week, say so directly: "no session logs found for this week — review isn't possible. run /end-session at the end of sessions to enable this."
- "Recommended Adjustments" must be specific and actionable. Never write "consider improving X." Write "cut X from P0" or "move X to P1" or "schedule a decision on X by Wednesday."
- Never write more than 3 recommended adjustments. Force prioritization.
