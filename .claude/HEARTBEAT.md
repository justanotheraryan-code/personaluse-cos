# Heartbeat — Session Startup

Run this automatically when the user opens a session without a specific task or ask. No prompt needed.

---

## Step 0 — Check if setup is needed

Read `context/me.md`. If the name field is empty or still contains `[Your Name]`, stop and run the setup skill:

> "looks like this is a fresh install. let's get you set up — it takes about 5 minutes."

Then invoke the `setup` skill. Do not proceed with the briefing below until setup is complete.

---

## Startup Sequence (after setup)

### 1. PRIORITIES

Read `context/current-priorities.md`.
- Note the `*Last updated:*` date at the top.
- Identify all P0 items. Count unchecked ones (`- [ ]`).
- Flag any P0 that is overdue (sprint end date has passed) or has appeared in 2+ recent session memory files under "Pending / Blocked" without progress.

### 2. MEMORY

Find all files matching `memory/YYYY-MM-DD.md`. Read the most recent one.
- Note what was in progress or left pending.
- Compute days since last session log: compare the file date to today.
- If no memory files exist, note: "no session history yet."

### 3. DECISIONS

Scan the last 3 entries in `decisions/log.md`. Note anything that affects current work or open P0s.

### 4. CONTENT

Read posting cadence from `context/work.md`.
- Check today's day of the week against the scheduled posting days.
- If today is a posting day, check `context/current-priorities.md` — is that day's content item checked or unchecked?
- If unchecked and no draft exists: flag as due.

### 5. INBOX (if context/inbox.md exists)

Read `context/inbox.md`. Flag any items marked with a date that is 3+ days before today and has no disposition (no `[pursue]`, `[pass]`, or `[defer]` tag).

### 6. METRICS (if context/metrics.md exists)

Scan `context/metrics.md`. Flag any row where the `as of` date is more than 7 days before today. Surface the metric name only — not the stale value.

### 7. RELATIONSHIPS (if context/relationships.md exists)

Read `context/relationships.md`. For each row, compare "Last contact" date against cadence:
- `weekly`: flag if last contact > 7 days ago
- `monthly`: flag if last contact > 30 days ago
- `quarterly`: flag if last contact > 90 days ago

Flag the person's name and how many days overdue the touchpoint is.

### 8. IDEAS BACKLOG (if projects/content-calendar/ideas.md exists)

Count unchecked items (`- [ ]`) in the "Raw Ideas" section of `projects/content-calendar/ideas.md`.
If count > 3: flag as "N ideas unprocessed — run /content-calendar to triage".

---

## Step 9 — DRIFT DETECTION

Compute these signals before surfacing the briefing:

**Priority staleness:**
If the `*Last updated:*` date in `current-priorities.md` is more than 7 days ago:
→ flag: `priorities last updated {N} days ago — run /plan-week`

**Memory gap:**
If the most recent session memory file is more than 2 days old (and today is a weekday):
→ flag: `no session log in {N} days — context may be stale`

**P0 stagnation:**
If a P0 item is unchecked AND appeared as "Pending / Blocked" in the last 2 session memory files with no progress noted:
→ flag: `[item] has been blocked {N} sessions — needs a decision`

**Goal drift:**
Read `context/goals.md`. If a quarterly goal has had no corresponding P0 or P1 item in `current-priorities.md` for the current week:
→ flag: `goal "[goal]" has no work scheduled this week`
(Only surface this if 2+ goals are drifting — don't nitpick one.)

---

## Step 11 — SURFACE

Give a max 9-line briefing. No prose. Signal only. Omit any line that has nothing to report.

```
> sprint:     [1-line status — what's on fire, what's on track]
> content:    [due today / next due / all clear]
> blockers:   [overdue P0s or "none"]
> last session: [1 line from memory — what was worked on]
> metrics:    [stale metrics, if any — or omit]
> people:     [overdue touchpoints, if any — or omit]
> ideas:      [N unprocessed ideas — or omit]
> drift:      [priority staleness / goal drift / memory gap — or "all current"]
> next action: [single most important thing to do right now]
```

If there are drift warnings:
```
// run /plan-week to reset the week
```
If relationships are flagged:
```
// run /meeting-prep [name] or send a quick note
```

After the briefing, wait for direction. Do not offer to help with everything at once.

---

## End-of-Session Reminder

If a substantive session has occurred (work done, decisions made, plans changed) and `/end-session` has not been run, remind the user before the conversation ends:

> "before you go — run /end-session to log this. takes 30 seconds and keeps memory fresh."

Only say this once. Don't repeat if they decline.

---

## Rules

- Summarize ruthlessly. 7 lines max for the briefing.
- Flag only what needs attention or a decision.
- If nothing is overdue or blocked, say so in one line. Don't pad.
- Computed drift signals are high-value — surface them even if they feel awkward.
- After the briefing, wait. Don't jump into suggestions.
