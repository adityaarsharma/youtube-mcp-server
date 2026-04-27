---
name: youtube-script
description: >
  Writes a retention-engineered tutorial script for WordPress/Elementor videos.
  Includes 3-part hook, pattern interrupts every 60-90 seconds, soft CTA placement,
  and retention risk map. Based on Wistia, Adobe, and AIR Media-Tech research.
---

# /youtube script

## Research Foundation
- **Wistia, 2024**: Pattern interrupts every 60–90s reduce drop-off 40%
- **Adobe Tutorials**: Structured "what you'll learn" intro → +43% completion
- **AIR Media-Tech**: 5 retention energy patterns: challenge, story, reveal, transformation, social proof
- **Retention Rabbit**: Hook sweet spot 28–42 seconds
- **YouTube Creator Academy**: Soft CTA at 25% of video = 3.2x subscription rate vs end-of-video CTA

## Script Structure

### PART 1 — HOOK (28–42 seconds)

Three-layer hook formula: **Grab → Promise → Stakes**

```
GRAB (5-8 sec): Visual or statement that stops the scroll.
  "Most WordPress sites look like this [show bad example]. Here's what it should look like."

PROMISE (10-15 sec): What they get by watching.
  "In the next 13 minutes, you'll have a full horizontal scroll website in Elementor —
   no CSS, no code, just clicks."

STAKES (10-15 sec): Why it matters or what they lose by skipping.
  "This exact layout is what agencies charge $3,000+ for. You can build it for free today."
```

**Hook Energy Patterns (pick 1 per video):**
| Pattern | When to Use | Example opener |
|---------|------------|----------------|
| Challenge | Feature is surprisingly easy | "This looks complex. It's 10 clicks." |
| Story | Relatable problem | "A client asked me to build this. I spent 3 hours before I found this." |
| Reveal | Show the result first | Play the finished website for 5 seconds, then say "Here's how." |
| Transformation | Before/after | Show broken/basic vs polished result |
| Social Proof | Authority signal | "This is how [brand] built their website." |

### PART 2 — INTRO FRAME (20-30 seconds)

After the hook, deliver the "What You'll Learn" as a spoken list — matches the description bullets and signals YouTube what to index.

```
"In this video you'll see:
— How to enable the horizontal scroll widget
— How to import a ready-made demo in one click
— How to add navigation, background transitions, and mobile responsiveness
Let's go."
```

### PART 3 — TUTORIAL BODY

Structure by action, not by UI location. Each segment = one viewer outcome.

**Segment template:**
```
[STATE THE GOAL OF THIS SEGMENT — 5 sec]
"Now we'll add the dots navigation so viewers can jump between sections."

[SHOW THE STEPS — 45-60 sec]

[PATTERN INTERRUPT — every 60-90 sec, pick one:]
- Quick result preview: "Here's what that looks like now."
- Tip callout: "Pro tip: if you're building for mobile, do this instead."
- Context add: "Why does this matter? Because without this..."
- Transition: "Now that X is done, here's what comes next."
```

### PART 4 — SOFT CTA (at 25% mark)

Place at the first natural pause point after ~25% of video length.

```
"If this is helpful so far, consider subscribing — we post new Elementor tutorials
every week and I'd hate for you to miss the next one."
[Continue tutorial immediately — don't dwell on CTA]
```

Research: 3.2x better than end-of-video CTA (YouTube Creator Academy, 2025).

### PART 5 — CONCLUSION (60-90 seconds)

```
[RESULT SHOWCASE — 20 sec]: Show the finished output in action.
[RECAP — 20 sec]: "You built X, Y, and Z today."
[NEXT STEP CTA — 20 sec]: Link to related video or product.
  "If you want to take this further, watch this next — it shows how to add
   page transition effects to this same layout."
[SUBSCRIBE CTA — 10 sec]: "Like this video if it helped, and subscribe for more."
```

## Output Format

Write the full script in this format:

```
## HOOK (0:00 – 0:35)
[Script text]

## INTRO FRAME (0:35 – 1:00)
[Script text]

## [SEGMENT NAME] (1:00 – X:XX)
[Script text]
[PATTERN INTERRUPT at ~60s]

## SOFT CTA (~25% mark)
[Script text]

## [REMAINING SEGMENTS]

## CONCLUSION
[Script text]

---
## RETENTION RISK MAP
| Timestamp | Risk | Fix |
|-----------|------|-----|
| ~2:00 | Screen stays on same menu for 90s | Cut to result preview |
| ~5:00 | Step-by-step gets repetitive | Add "pro tip" callout |
```
