# Chief of Staff — A Claude Code EA Template

Every session, you re-explain yourself to your AI assistant.

Your role. Your team. What's on fire this week. Which side project you can't name publicly. What tone you write in. Over and over.

This repo fixes that.

**Chief of Staff** is a ready-to-clone Claude Code workspace that turns Claude into a personal EA who already knows you — your work, your team, your priorities, your content voice. You set it up once. Every session after that, Claude briefs you instead of the other way around.

---

## What it does

**On every session open**, Claude reads your context and gives you a 5-line brief:
- What's on fire this sprint
- Whether a content post is due today or tomorrow
- What was left pending from your last session
- One suggested next action

No prompt needed. It just happens.

**When you ask for help**, it already knows:
- Which projects you're running and who owns what
- Your team structure and how you communicate
- Your content pillars, posting cadence, and the way you actually write
- Your quarterly goals and this week's P0s

**Skills you can invoke:**
- `/draft-linkedin-post` — drafts a post in your voice, from a topic or angle
- `/sprint-summary` — pulls your GitHub boards and surfaces blockers by workstream
- `/setup` — the first-time onboarding wizard (only needed once)

**It gets smarter over time** through a feedback log (content corrections), a decision log (why you chose what), and session memory files that carry forward what was in progress.

---

## Who this is for

Founders, PMs, and builders who run multiple parallel tracks — a day job, a side project, content, advising, admin — and want an assistant that's already loaded with context when they sit down to work.

If you've ever opened a ChatGPT or Claude session and spent the first five minutes explaining who you are and what you're building, this is for you.

---

## How it works

The repo is structured so Claude reads your context files on startup — who you are, what you're working on, your team, your goals. Those files live in `context/`. You fill them in once (via the setup wizard). Claude references them every session.

Skills are reusable workflows stored as markdown files in `.claude/skills/`. When you ask Claude to "draft a post" or "summarize the sprint," it finds the matching skill, reads the instructions, and executes them against your context.

Memory works the same way — session notes live in `memory/YYYY-MM-DD.md`, and Claude reads the most recent one at startup to pick up where you left off.

---

## Setup

**Prerequisites:** [Claude Code](https://claude.ai/code) installed. Takes about 5 minutes.

### 1. Clone the repo

```bash
git clone https://github.com/shivamtiwari3/Chiefofstaff.git my-chief-of-staff
cd my-chief-of-staff
```

### 2. Open in Claude Code

```bash
claude .
```

### 3. Type "start"

Claude will detect that your context is empty and walk you through setup — about 10 questions, one at a time. It writes your answers directly into the context files.

That's it. Every session after this, Claude briefs you automatically.

---

## Keeping it current

| Cadence | What to update |
|---------|----------------|
| Weekly | `context/current-priorities.md` — your sprint |
| Quarterly | `context/goals.md` — your goals |
| Anytime | Say "remember that I always want X" to save a preference |
| After a decision | Ask Claude to log it to `decisions/log.md` |

---

## Repo structure

```
├── CLAUDE.md                      # EA instructions — Claude reads this on startup
├── CLAUDE.local.md                # Your private overrides (gitignored)
├── .claude/
│   ├── HEARTBEAT.md               # Session startup logic
│   ├── FEEDBACK-LOG.md            # Content correction history
│   ├── rules/
│   │   ├── content-style.md       # Your content voice, pillars, hook formulas
│   │   └── communication-style.md
│   └── skills/
│       ├── setup/                 # Onboarding wizard
│       ├── draft-linkedin-post/   # Post drafting skill
│       └── sprint-summary/        # Sprint summary skill
├── context/
│   ├── me.md                      # Who you are
│   ├── work.md                    # Your workstreams + GitHub boards
│   ├── team.md                    # Your team
│   ├── current-priorities.md      # This week's P0s + P1s
│   └── goals.md                   # Quarterly goals
├── decisions/log.md               # Append-only decision log
├── memory/                        # Session logs (gitignored, only template tracked)
├── projects/                      # One subfolder per workstream
├── references/                    # SOPs, examples
└── templates/                     # Reusable templates
```

---

## Adding your own skills

When you find yourself explaining the same workflow to Claude more than twice, turn it into a skill.

Create a file at `.claude/skills/your-skill-name/SKILL.md` and describe the steps. Claude Code will pick it up automatically. You can trigger it by name or just describe what you want.

Examples worth building:
- `invoice-tracker` — check pending invoices and draft follow-up messages
- `meeting-prep` — pull context for an upcoming meeting
- `session-summary` — end-of-day recap across all your tracks
- `draft-instagram-post` — adapt a LinkedIn post for Instagram

---

## GitHub board integration

Sprint summaries pull from GitHub Projects. After setup, add your board IDs and org names to `context/work.md`. Requires the `gh` CLI:

```bash
gh auth login
```

---

## License

MIT. Fork it, adapt it, make it yours.

Built by [Shivam Tiwari](https://linkedin.com/in/shivamtiwariin).