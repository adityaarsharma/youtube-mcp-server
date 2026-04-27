---
name: youtube-batch-seo
description: >
  Bulk SEO update for existing video library. Uses get_low_ctr_videos to find
  lowest-performing videos, then generates optimized metadata and pushes updates
  via batch_seo_update. Prioritises by views, age, or CTR.
---

# /youtube batch-seo

## What Makes This Different From VidIQ/TubeBuddy
- Pulls real-time keyword data from DataForSEO for every video, not cached suggestions
- Enforces YouTube policy guardrails automatically — no manual review needed
- Pushes updates directly to YouTube — no copy-paste
- Prioritises by actual lowest-performing videos first, not random

## Workflow

### STEP 1 — Find Candidates
Use `youtube-marketing-mcp:get_low_ctr_videos` with:
- `limit`: 10-20 videos
- `sort_by`: "views" (default) or "age" for freshness plays
- `days_old_min`: 90 (avoid updating videos still in early indexing phase)

### STEP 2 — Analyse Each Video
For each candidate:
1. Pull current metadata with `get_video_details`
2. Identify the primary keyword from current title
3. Run `dfs-mcp:kw_data_google_ads_search_volume` on current keyword
4. Run `dfs-mcp:serp_youtube_organic_live_advanced` to check where video currently ranks
5. Identify the gap: is the title missing the best keyword? Is the description missing "WHAT YOU'LL LEARN"?

### STEP 3 — KEYWORD PROTECTION RULE (Critical)
Before changing any metadata on an existing ranking video:
1. Note any keywords where the video ranks top 20
2. These keywords MUST stay in the new title, description, and tags
3. New SEO = superset of existing ranking terms, not replacement

### STEP 4 — Generate Updates
For each video, produce:
- New title (if current title is underoptimised)
- New description opening (first 200 chars = most important)
- New WHAT YOU'LL LEARN section if missing
- Updated tags (remove zero-volume, add high-volume gaps)

### STEP 5 — Push via MCP
Use `youtube-marketing-mcp:batch_seo_update` with all updates array.
Server handles rate limiting automatically (500ms delay between updates).

## Prioritisation Logic

| Priority | Signal | Action |
|----------|--------|--------|
| 🔴 Highest | Video has 0 WHAT YOU'LL LEARN section | Add immediately — biggest indexing gap |
| 🔴 Highest | Title has no year, top competitor has year | Add 2026 |
| 🟡 Medium | Primary keyword not in first 40 chars of title | Reorder |
| 🟡 Medium | Description opening doesn't start with keyword | Rewrite first 150 chars |
| 🟢 Lower | Tags include zero-volume keywords | Replace with DataForSEO-verified terms |

## Output Format

```
## BATCH SEO REPORT

### Candidates Found: [N videos]
Sorted by: [views/CTR/age]
Date range: Videos older than [X] days

---

### VIDEO 1: [Title]
URL: [url]
Current views: [n] | Published: [date]
Primary keyword: [keyword] | Monthly vol: [n]
SERP rank: [#X or not ranking]

ISSUES:
- [Issue 1]
- [Issue 2]

UPDATES:
Title: [new title]
Description opening: [new first 200 chars]
Tags added: [new tags]
Tags removed: [removed tags]

Status: [QUEUED / SKIPPED — reason]

---

[Repeat for each video]

---
### PUSHING UPDATES...
[Results from batch_seo_update]

### SUMMARY
Updated: [N]
Skipped (policy block): [N]
Skipped (already optimal): [N]
```
