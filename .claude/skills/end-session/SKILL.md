# Skill: end-session

Capture what happened this session and write it to memory.

## When to Use

Triggered by `/end-session`, "wrap up", "end session", "log today", "save session".

Also trigger proactively: if a substantive session occurred (work done, decisions made, plans changed) and the user hasn't run this, remind them before they close:
> "before you go — want me to log this session? takes 30 seconds."

---

## Steps

### 1. Scan the Session

Review the current conversation for:
- What was worked on or completed
- Decisions made (and the reasoning if discussed)
- Items left pending, blocked, or explicitly deferred
- What the user said they'd work on next

Don't ask if you can infer it. Fill in what you know.

### 2. Draft the Log Entry

Use today's date (YYYY-MM-DD). Draft:

```
# YYYY-MM-DD

## Worked On
- [item]

## Decisions Made
- [decision] — [reasoning if known]

## Pending / Blocked
- [item]

## Tomorrow
- [item]
```

Show the draft. Ask: "anything to add, change, or remove?"

If the session was light (e.g. only a quick question was answered), keep the log minimal. Don't pad it.

### 3. Write the File

After user confirms (or says "looks good"), write to `memory/YYYY-MM-DD.md`.

Confirm with one line:
> "> session logged → memory/YYYY-MM-DD.md"

### 4. Decision Log Check

If any decisions were made that aren't already in `decisions/log.md`, ask:
> "want to log any decisions to decisions/log.md?"

If yes, append entries in this format:
```
[YYYY-MM-DD] DECISION: ... | REASONING: ... | CONTEXT: ...
```

Only ask once. Don't push it if they say no.

### 5. Priorities Sync

If any P0 or P1 items were completed this session, ask:
> "want me to check those off in current-priorities.md?"

If yes, update `context/current-priorities.md` — mark the completed items with `- [x]`.

### 6. Feedback Log Check

If content was drafted and the user gave corrections or style notes, ask:
> "any corrections from this draft to lock in for next time?"

If yes, append to `.claude/FEEDBACK-LOG.md`:
```
[YYYY-MM-DD] CORRECTION: [what was wrong] | WAS: [old pattern] | NOW: [correct pattern]
```

---

## Rules

- Never write a session log without user confirmation on the draft.
- Keep it factual. No commentary, no summaries of summaries.
- If nothing meaningful happened, say so: "> light session — nothing to log."
- The memory file is personal and gitignored. Write freely.
