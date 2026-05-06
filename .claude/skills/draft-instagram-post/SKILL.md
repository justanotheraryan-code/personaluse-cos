# Skill: draft-instagram-post

Adapt a LinkedIn post (or topic) for Instagram — tighter, visual-first, different audience.

## When to Use

Triggered by `/draft-instagram-post`, "adapt this for Instagram", "make an Instagram version of this post", "draft an IG post about X".

---

## Steps

### 1. Get the Source

Two cases:

**Case A — Adapting an existing LinkedIn post:**
If a LinkedIn post was just drafted in this session or the user pastes one, use it as the source.
Extract the core idea, the key data point or insight, and the CTA direction.

**Case B — Fresh topic:**
Ask: "what's the topic or angle? is this from a specific LinkedIn post, or starting fresh?"
Then follow the same LinkedIn post drafting logic (read content-style.md) before adapting.

### 2. Read Style Rules

Read `.claude/rules/content-style.md` — Instagram adaptation section.
Read `.claude/FEEDBACK-LOG.md` — check for any corrections that apply to Instagram too.

### 3. Draft the Instagram Post

Instagram format is structurally different from LinkedIn:

**Hook (line 1):**
Single punchy line. No setup. No context. Just the sharpest possible opener.
On Instagram, the hook is the caption above "more" — make it worth the tap.

**Body:**
3–5 bullet points or short fragments. No paragraphs.
Each line should be a standalone thought — people scan, not read.
Visual-first framing: write as if the post is a carousel and each bullet is a slide.

**CTA:**
1 line. A direction, not a question. Make it specific to the content.
Examples: "save this for your next sprint" / "go build the thing" / "read the full thread, link in bio"

**Hashtags:**
8–12. Mix:
- 3–4 niche tags (specific to topic)
- 3–4 mid-range tags (topic area, e.g. #AIagents, #ProductBuilding)
- 2–3 broad tags (e.g. #startup, #founder, #buildinpublic)

**Hard rules (same as LinkedIn, stricter on format):**
- All lowercase
- No em dashes
- No "I'm excited to share" or transitions
- No emojis in the body text (profile can have them, body can't)
- Max 150 words in the body

**Structure output:**
```
[HOOK]

[BODY — bullet or fragment per line]

[CTA]

.
.
.
[HASHTAGS]
```

The three dots create visual separation from hashtags in the caption.

### 4. Add Visual Direction

After the caption, add a brief visual brief in brackets — not part of the post:

```
[VISUAL: carousel — slide 1: [hook as headline], slides 2-5: [one bullet each], slide 6: [CTA]]
[or]
[VISUAL: single graphic — [what it should show]]
```

This isn't posted — it's a note for when you create the visual.

### 5. Present the Draft

Show the full caption + visual direction. Ask:
"want to adjust the hook, bullets, or hashtags? or does this work?"

Handle edits section by section — don't rewrite the whole post unless asked.

---

## Rules

- Instagram ≠ shorter LinkedIn. It's a different format. Don't just truncate — restructure.
- The hook is even more critical on Instagram because of the fold. Spend extra time on it.
- Bullet points should feel like slides in a carousel — each one standalone.
- If adapting from LinkedIn, keep the core insight but rewrite the structure entirely.
- Visual direction is mandatory — always include it, even if brief.
