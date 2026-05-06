# Skill: meeting-prep

Load full context before a meeting so you walk in sharp, not scrambling.

## When to Use

Triggered by `/meeting-prep [person or topic]`, "prep for my call with X", "what do I need before meeting with X", "brief me on X before we talk".

If no person or topic is given, ask: "who's the meeting with, and what's it about?"

---

## Steps

### 1. Identify the Meeting

Extract:
- **Who**: person name(s) or company
- **What**: meeting type (1:1, investor call, partner discussion, team standup, sales call, etc.)
- **When**: if mentioned — note if it's today or imminent

### 2. Pull Context (run in parallel)

**From `context/team.md`:**
Search for the person by name. Extract their role, any notes, and communication channel.

**From `context/current-priorities.md`:**
Look for any items that involve or are blocked by this person. Flag open asks.

**From `decisions/log.md`:**
Search for entries that mention this person or the meeting topic. Surface decisions already made — prevents relitigating.

**From `context/work.md`:**
If the meeting is about a specific project or track, pull the relevant section.

**From recent `memory/YYYY-MM-DD.md` files (last 7 days):**
Search for any mention of this person or topic. Note: last interaction, what was discussed, what was left open.

**From `projects/` folder:**
If the meeting is about a specific project, read that project's README.

### 3. Build the Brief

Output in this exact format:

```
## MEETING BRIEF — [Person / Topic]
// [meeting type] — [date/time if known]

### WHO
[Name] — [Role] — [Company if external]
[Any relevant background, relationship context, or notes from team.md]

### CONTEXT
[Current state of the relevant project or relationship — 2-4 bullets max]
[What they last touched or were waiting on — from session memory]

### OPEN ITEMS
[Anything in current-priorities.md that involves them or is blocked by them]
[Questions you asked in a previous session that are still unanswered]

### DECISIONS ALREADY MADE
[Relevant entries from decisions/log.md — so you don't walk in and relitigate]
[If none: "no prior decisions logged on this topic"]

### AGENDA (suggested)
1. [most important thing to cover — decision, ask, or update]
2. [second item]
3. [any standing items or housekeeping]

### PUSH FOR
[Specific decision or outcome you want from this meeting — be concrete]
[What does "this meeting was useful" look like?]

### QUESTIONS TO ASK
- [question]
- [question]

### WATCH OUT FOR
[Known sensitivities, past friction, or things that tend to derail — from memory or notes]
[If nothing logged: omit this section]
```

Keep it tight. If you don't have context for a section, skip it — don't pad with guesses.

### 4. Offer to Log Outcomes

After the meeting (if the user comes back), offer:
> "want to log what came out of this? i can add decisions to the decision log and update current-priorities.md."

---

## Rules

- Never fabricate context you don't have. Say "nothing logged on this person/topic" if the files are empty.
- If context files are all placeholders (setup not run), tell the user: "no context loaded yet — run /setup first."
- The brief should be readable in under 2 minutes. Cut anything that's just noise.
- "Push For" is the most important section — always include it if you can infer the goal.
