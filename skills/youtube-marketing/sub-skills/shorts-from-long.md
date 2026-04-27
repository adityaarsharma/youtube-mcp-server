---
name: youtube-shorts-from-long
description: >
  Extracts 3-5 Shorts-worthy moments from an existing long-form video.
  Uses transcript analysis to find the best clips, writes Shorts scripts,
  and generates metadata for each. Accounts for March 2025 view reform and
  September 2025 freshness decay rules.
---

# /youtube shorts-from-long

## Research Foundation
- **YouTube, March 2025**: Shorts views now count toward channel total; separate feed algorithm
- **YouTube, September 2025**: Freshness decay — Shorts drop 60% distribution after 28–30 days; don't use Shorts for evergreen content
- **Social Insider, 2025**: Shorts that tease long-form video → +28% long-form views

## What Makes a Good Shorts Clip

| Signal | Good Clip | Bad Clip |
|--------|-----------|----------|
| Hook in first 2 seconds | Has immediate visual hook | Starts with intro talking |
| Self-contained | Makes sense without context | References earlier part |
| Wow moment | Shows impressive result | Setup/explanation only |
| Length | 30–55 seconds optimal | >60s for simple tips |
| CTA potential | Natural "watch the full tutorial" moment | No clear next step |

## Workflow

### STEP 1 — Get Video Data
Use `get_video_details` to pull timestamps and description.
If transcript is available: analyze for hook moments, result reveals, tips.

### STEP 2 — Identify 5 Clip Types

**Type 1 — RESULT REVEAL** (~15–30 sec)
The moment where the finished result appears for the first time.
Best Shorts type — shows what's possible, drives full-video clicks.

**Type 2 — PRO TIP** (~30–45 sec)
One standalone tip that saves time or solves a common problem.
Self-contained, high-share potential.

**Type 3 — BEFORE/AFTER** (~20–40 sec)
Cut between the plain Elementor default and the finished widget result.
Strong visual contrast = high completion rate.

**Type 4 — COMMON MISTAKE** (~30–50 sec)
"Don't do this — do this instead."
Problem-solution format works well in Shorts feed.

**Type 5 — QUICK WIN** (~20–30 sec)
The fastest, most impressive feature of the widget.
Optimized for discovery — broad audience appeal.

### STEP 3 — Write Each Short

```
[VISUAL: First frame must be the result or hook — no talking head for 5+ seconds]
[0:00–0:03] Hook statement (no intro, no "hi guys")
[0:03–end] Deliver the value
[Last 3 sec] CTA: "Full tutorial → link in bio" or "Subscribe for more"
```

### STEP 4 — Metadata for Each Short

- **Title**: Under 60 chars, keyword first
- **Description**: 2-3 sentences + link to long-form video
- **Tags**: Include "shorts" + main topic keyword
- **Hashtags**: #shorts #elementor #wordpress + 2 topic-specific

## Output Format

```
## SHORTS PLAN FOR: [Long Video Title]
Source video: [URL]
Shorts identified: [N]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
### SHORT 1: [Title]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Type: [Result Reveal / Pro Tip / Before-After / Mistake / Quick Win]
Source timestamp: [start] – [end]
Length: [X] seconds

Script:
[Full spoken script with visual notes]

Metadata:
Title: [Short title]
Description: [2-3 sentences]
Tags: [tags including "shorts"]
Hashtags: #shorts #[topic] #elementor

[Repeat for each Short]
```
