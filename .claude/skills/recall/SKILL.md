# Skill: recall

Search across all memory, decisions, and project history to surface what you already know about a topic.

## When to Use

Triggered by `/recall [topic]`, "what do we know about X", "have I dealt with this before", "what did I decide about X", "remind me what happened with X", "did I ever work on Y".

If no topic is given, ask: "what do you want me to search for?"

---

## Steps

### 1. Parse the Query

Identify:
- **Topic/keyword**: the main thing to search for (person, project, technology, decision area, company, etc.)
- **Time scope**: if the user mentioned "recently", "last month", "ever" — note it
- **Type of recall**: are they looking for a decision? a past work item? a person? a lesson learned?

### 2. Search All Sources (run in parallel)

Search each source for any mention of the topic keyword(s):

**Session memory** (`memory/YYYY-MM-DD.md` files):
Search all dated files. Extract: date, which section it appeared in (Worked On / Decisions / Blocked / Tomorrow), and the relevant line(s).

**Decision log** (`decisions/log.md`):
Search all entries. If a decision entry mentions the topic, extract the full entry: date, decision, reasoning, context.

**Feedback log** (`.claude/FEEDBACK-LOG.md`):
Search for any corrections related to the topic (relevant for content-related recalls).

**Current priorities** (`context/current-priorities.md`):
Check if the topic is an active item right now.

**Project files** (`projects/*/README.md`):
Search all project READMEs for the topic.

**Context files** (`context/team.md`, `context/work.md`):
Check if the topic is a person, project, or tool mentioned in core context.

### 3. Synthesize and Output

Group results by source. Most recent first within each group.

```
## RECALL — "[topic]"
// searched: memory, decisions, feedback, projects, context

---

### DECISIONS MADE
[YYYY-MM-DD] [decision] — [reasoning]
[or: "no decisions logged on this topic"]

### PAST WORK
[YYYY-MM-DD] — [what was worked on / what happened]
[YYYY-MM-DD] — ...

### BLOCKERS / PENDING (historical)
[YYYY-MM-DD] — [item that was stuck]
[or: "none found"]

### ACTIVE RIGHT NOW
[item from current-priorities.md, if any]
[or: "not in current priorities"]

### LESSONS / CORRECTIONS
[from FEEDBACK-LOG, if relevant]
[or: "none logged"]
```

If nothing is found in any source:
> "no records found for '[topic]'. this either hasn't come up before or predates the session logs."

### 4. Surface the Most Useful Thing

After the results, in one line, surface the single most actionable piece of context:
> "most relevant: [decision / lesson / last touchpoint] from [date]"

If the results suggest a decision should be revisited or a blocker keeps recurring, flag it:
> "note: '[item]' has appeared as blocked [N] times. might be worth a decision."

---

## Rules

- Search broadly, summarize tightly. Don't paste raw file contents.
- If session memory files are sparse or absent, say so: "only [N] session logs exist — history before [earliest date] isn't searchable."
- Never guess or infer what "probably" happened. Only surface what's actually in the files.
- The output should answer: "what do I already know about this that's relevant right now?"
- Keep total output under 30 lines. If results are extensive, summarize and offer to go deeper on a specific source.
