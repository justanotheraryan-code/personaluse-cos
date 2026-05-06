# Skill: content-calendar

Audit the content schedule, surface gaps, and suggest topics from what's actually happening in your work.

## When to Use

Triggered by `/content-calendar`, "what's my content schedule look like", "what posts are due", "content gaps", "what should I write about this week".

---

## Steps

### 1. Load Content Context (run in parallel)

- `context/work.md` — posting cadence (days/week), pillar schedule, topics
- `context/current-priorities.md` — this week's content items (what's checked vs. unchecked)
- `projects/content-calendar/README.md` — planned posts, pillar tracking
- `projects/content-calendar/ideas.md` — if it exists, unprocessed ideas
- `.claude/rules/content-style.md` — pillar definitions and voice rules
- Recent `memory/YYYY-MM-DD.md` files (last 14 days) — extract any mentions of posts drafted, published, or planned

### 2. Reconstruct the Calendar

From the above, build a picture of:

**Published recently** — posts that appear in session memory as drafted + published (last 14 days). Group by pillar.

**Planned but not drafted** — posts in current-priorities.md marked `- [ ]`. Flag if past their due day.

**Pillar coverage** — for each pillar defined in content-style.md:
- When was the last post in this pillar published?
- If >7 days: flag as neglected
- If >14 days: flag as cold

**Ideas backlog** — count of unprocessed items in `projects/content-calendar/ideas.md` (if the file exists).

### 3. Suggest Topics from Current Work

Read `context/work.md` (active projects, what's shipping) and recent session memories (what was worked on this week). Cross-reference with content pillars.

Generate 3 topic suggestions that:
- Come from real work happening right now (not generic industry takes)
- Map to a specific pillar
- Could be drafted today

Format each as:
```
[PILLAR] — [Hook angle / first line concept]
Source: [what in your work this comes from]
Formula: [suggested hook formula from content-style.md]
```

### 4. Output the Calendar View

```
## CONTENT CALENDAR — Week of YYYY-MM-DD

### THIS WEEK
- [ ] [Day] — [topic / pillar] — [status: not started / drafted / published]

### OVERDUE
- [Day that passed] — [topic] — [N days overdue]

---

### PILLAR HEALTH
- [Pillar name]: last post [N] days ago — [OK / NEGLECTED / COLD]

### IDEAS BACKLOG
[N] unprocessed ideas in ideas.md
[If 0 or file doesn't exist: "no ideas backlog"]

---

### SUGGESTED TOPICS (from current work)
1. [PILLAR] — [hook angle]
   Source: [what in your work]
   Formula: [hook formula]

2. ...

3. ...
```

### 5. Offer Next Steps

After showing the calendar:
> "want to draft any of these? say `/draft-linkedin-post` and I'll start from one of the suggestions."

If there are overdue posts:
> "want me to flag the overdue ones in current-priorities.md?"

---

## Rules

- Topic suggestions must be grounded in real current work from the user's context files — no generic "here are 3 AI takes" suggestions.
- If content-style.md pillars are still placeholder text (not filled in), say: "content pillars aren't defined yet — fill in `.claude/rules/content-style.md` first."
- Pillar health is the most actionable section. Lead with it if something is cold.
- Never suggest the same topic type two weeks in a row — check recent memory to avoid repetition.
