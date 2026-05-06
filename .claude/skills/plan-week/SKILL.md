# Skill: plan-week

Set weekly P0s/P1s that are actually aligned to quarterly goals.

## When to Use

Triggered by `/plan-week`, "plan this week", "what should I focus on this week", "set weekly priorities".

Best run every Monday before starting work. Also useful mid-week if priorities feel unclear or the drift check flagged stale priorities.

---

## Steps

### 1. Load Context (run in parallel)

Read all of these:
- `context/goals.md` — quarterly goals
- `context/current-priorities.md` — last week's state (done vs. not done)
- `context/work.md` — active projects, posting cadence, sprint board IDs
- `decisions/log.md` — last 5 entries (anything that shifts what matters)
- `context/inbox.md` — if it exists, items needing disposition

Find the most recent 5 files in `memory/` (pattern: `YYYY-MM-DD.md`, sorted by date descending). Read them. Extract:
- What was worked on repeatedly (signal: high priority)
- What was blocked repeatedly (signal: needs a decision or removal)
- What was in "Tomorrow" but never became "Worked On" (signal: avoidance or bad scope)

### 2. Analyze

Before drafting, answer these internally:

**Carry-forwards:**
Which P0s from last week are unchecked? Are they still P0, or should they be downgraded?

**Goal alignment:**
For each goal in `goals.md`, is there at least one P0 or P1 this week that moves it forward?
If a goal has had no scheduled work for 2+ weeks, flag it as drifting.

**Stale blockers:**
If an item has appeared as "Pending / Blocked" in 3+ session memory files, it is either:
a) A real blocker that needs a decision — surface it
b) Something that should be removed — ask the user

**Content:**
What posts are due this week based on cadence in `context/work.md`? List them by day with pillar.

**Inbox:**
Any items in `context/inbox.md` with no disposition that are >3 days old? Recommend pursue/pass/defer for each.

### 3. Draft the Week Plan

Output a complete replacement for `context/current-priorities.md`:

```
# Current Priorities

*Last updated: YYYY-MM-DD*

---

## [Work Track] — Week of YYYY-MM-DD

### P0 — Ship this week
- [ ] [item] — [owner]

### P1 — Important this week
- [ ] [item] — [owner]

---

## Personal — This Week

### Content
- [ ] [Day] — [topic / pillar]

### Side Project
- [ ] [item]

### Inbound / Opportunities
- [ ] [item] — [source, added YYYY-MM-DD]

### Admin
- [ ] [item]

---

*To refresh from GitHub: `gh project item-list BOARD_ID --owner ORG --format json`*
```

**Goal drift warnings** — append after the plan if any goals are drifting:

```
// GOAL DRIFT DETECTED
// "[goal]" — no scheduled work in 2+ weeks
// add a P1 this week or accept the tradeoff
```

### 4. Present and Confirm

Show the full draft. Point out:
- Any items you're flagging as stale blockers that need a decision
- Any goals with no coverage this week
- Carry-forwards you downgraded (explain why)

Ask: "does this look right? anything to add or cut?"

Handle edits. Don't rewrite the whole plan unless asked.

### 5. Write the File

After confirmation, overwrite `context/current-priorities.md` with the final plan.
Make sure `*Last updated:*` is set to today's date.

Confirm:
> "> week locked. current-priorities.md updated."

---

## Rules

- Never write to current-priorities.md without user confirmation.
- Don't just copy last week's unchecked items — interrogate whether they're still P0.
- If the user hasn't run `/setup`, this skill has no context to work from. Prompt setup first.
- Keep the plan tight. A P0 list longer than 5 items is a lie — help the user cut.
- The point is alignment: quarterly goals → weekly P0s → daily work. Make that chain visible.
