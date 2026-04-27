---
name: youtube-audit
description: >
  Full channel health audit across 4 dimensions: SEO, performance, content strategy,
  and monetization/funnel. Returns letter grades A-F with 30-day action plan.
---

# /youtube audit

## Input Needed
Pull automatically using MCP tools — no manual input required.

## 4-Dimension Audit Framework

### DIMENSION 1 — Technical SEO (Grade A–F)
Pull: last 30 videos via `get_all_videos`, check each for:

| Check | Weight | How to Evaluate |
|-------|--------|----------------|
| Primary keyword in title first 40 chars | HIGH | String check |
| Description has WHAT YOU'LL LEARN section | HIGH | Check for ✅ bullets |
| Timestamps present | MEDIUM | Check for 00:00 format |
| Tags count 15–20 | MEDIUM | Count tags |
| Title under 60 chars (full visibility) | MEDIUM | Length check |
| Year in title | LOW | Check for 2025/2026 |
| VideoObject schema on companion post | LOW | Check via wp-post existence |

**Grading:**
- A: 90%+ of videos pass all HIGH checks
- B: 75%+ pass all HIGH checks
- C: 50%+ pass
- D: <50% pass
- F: Most videos missing descriptions/timestamps/WHAT YOU'LL LEARN

### DIMENSION 2 — Performance (Grade A–F)
Pull: `get_analytics` for last 90 days, `get_top_videos`, `get_traffic_sources`

| Metric | Grade A | Grade B | Grade C | Grade D |
|--------|---------|---------|---------|---------|
| CTR | >6% | 4–6% | 2–4% | <2% |
| Avg view duration | >50% | 35–50% | 20–35% | <20% |
| Sub/view ratio | >0.5% | 0.2–0.5% | 0.1–0.2% | <0.1% |
| YouTube Search % | >40% | 25–40% | 15–25% | <15% |
| Impressions trend | Growing | Stable | Declining | Crashing |

### DIMENSION 3 — Content Strategy (Grade A–F)
Analyse last 20 videos for:

| Check | Good | Problem |
|-------|------|---------|
| Broad:Widget ratio | 2:1 | All widget-specific |
| Upload consistency | Every 5–7 days | Gaps >14 days |
| Topic variety | Mix of How-to + Widget + Broad | Only one type |
| Title differentiation | Unique angles | Same formula repeatedly |
| Shorts presence | 1–2 Shorts/week | No Shorts |

### DIMENSION 4 — Funnel (Grade A–F)
Check across last 20 videos:

| Check | Good | Problem |
|-------|------|---------|
| Widget page link in description | Present | Missing |
| Docs link in description | Present | Missing |
| CTA in script at 25% mark | Present | Only end CTA |
| End screen to related video | Present | No end screen |
| Subscribe CTA with sub_confirmation=1 | Present | Missing |
| Discount code mentioned | Present | Missing |

## Output Format

```
# CHANNEL AUDIT — [Channel Name]
Date: [today]
Data range: Last 90 days

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## SCORECARD

| Dimension | Grade | Score |
|-----------|-------|-------|
| Technical SEO | [A-F] | [X/10] |
| Performance | [A-F] | [X/10] |
| Content Strategy | [A-F] | [X/10] |
| Funnel | [A-F] | [X/10] |
| **OVERALL** | **[A-F]** | **[X/40]** |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## CRITICAL ISSUES (fix immediately)
1. [Issue + specific video or pattern]
2. [Issue]

## QUICK WINS (fix this week, 30 min each)
1. [Win + action]
2. [Win]

## 30-DAY ACTION PLAN
Week 1: [Specific actions]
Week 2: [Specific actions]
Week 3: [Specific actions]
Week 4: [Specific actions]

## PROJECTIONS (if actions completed)
CTR: [current]% → [projected]%
Monthly views: [current] → [projected]
Monthly subs: [current] → [projected]
```
