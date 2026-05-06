# Skill: triage

Score any inbound opportunity against your goals and bandwidth before it steals your attention.

## When to Use

Triggered by `/triage [opportunity]`, "should I do X?", "is this worth pursuing?", "someone asked me to Y — what do you think?", "quick take on this opportunity".

If no opportunity is described, ask: "what's the opportunity? describe it in a sentence or two."

---

## Steps

### 1. Capture the Opportunity

Extract:
- **What it is**: type (speaking gig, partnership, new client, advisory role, collab, project, etc.)
- **Who's asking**: person or org (if known)
- **Time cost**: how much time would this require? (if mentioned)
- **Deadline**: when does the decision need to be made?
- **Upside**: what's the stated or implied benefit?

If any of these are unclear, ask one clarifying question before proceeding. Not multiple — one.

### 2. Load Scoring Context (run in parallel)

Read:
- `context/goals.md` — quarterly goals (what actually matters right now)
- `context/current-priorities.md` — current P0/P1 load (is there real capacity?)
- `context/inbox.md` — other pending inbound (what else is already in play?)
- `decisions/log.md` — last 5 entries (any relevant past decisions on similar opportunities?)

### 3. Score on Three Axes

**Axis 1 — Goal Alignment (0–3)**
Does this opportunity move at least one quarterly goal forward, directly?
- 3: Direct path to a stated goal
- 2: Indirect but credible connection
- 1: Loosely related, stretch
- 0: No connection to current goals

**Axis 2 — Bandwidth Cost (low / medium / high)**
Given current P0 load in `current-priorities.md`:
- Low: fits in margins, no P0s affected
- Medium: requires carving out time, may slow a P1
- High: displaces a P0 or requires significant ongoing commitment

**Axis 3 — Timing (now / next quarter / never)**
Is this the right moment?
- Now: goals and context align, opportunity is time-sensitive
- Next quarter: good fit but wrong timing — better when current sprint clears
- Never: misaligned regardless of timing

### 4. Render the Verdict

```
## TRIAGE — [Opportunity Name]

VERDICT: [PURSUE / PASS / DEFER]

Alignment:  [score]/3 — [1-line reason]
Bandwidth:  [low/medium/high] — [1-line reason]
Timing:     [now/next quarter/never] — [1-line reason]

REASONING:
[2-3 sentences. Be direct. If it's a pass, say why clearly — not diplomatically.]

[If DEFER]: revisit when: [specific trigger or date, not "someday"]
[If PURSUE]: suggested next action: [specific first step]
```

**Scoring guide:**
- Alignment ≥ 2 + Bandwidth low/medium + Timing now → **PURSUE**
- Alignment ≤ 1 or Timing never → **PASS**
- Good alignment but Bandwidth high or Timing next quarter → **DEFER**

Override the formula if the reasoning is obvious — the score is a thinking tool, not the answer.

### 5. Offer to Log

After the verdict:
> "want to add this to inbox.md with the disposition? or log it as a decision if you've made the call?"

If yes:
- Add to `context/inbox.md` under Decided: `- [x] [YYYY-MM-DD] [opportunity] — [source] — [pursue/pass/defer]`
- Optionally append to `decisions/log.md`: `[YYYY-MM-DD] DECISION: pass/pursue on [X] | REASONING: ... | CONTEXT: ...`

---

## Rules

- Never say "it depends" as the verdict. Pick one.
- The reasoning must reference the user's actual goals from `goals.md` — not generic productivity advice.
- If context files are empty (setup not run), you can still triage but flag that the scoring is based on the conversation only, not loaded context.
- A deferred opportunity with no specific revisit trigger is just a polite pass. Say so.
- The point is a fast, confident decision — not a comprehensive analysis. Keep the whole output under 20 lines.
