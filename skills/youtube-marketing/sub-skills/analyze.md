---
name: youtube-analyze
description: >
  Deep analytics diagnosis for your YouTube channel. Interprets CTR, retention,
  traffic sources, subscriber conversion funnel, and revenue signals. Returns
  prioritised action list. Pulls live data from YouTube Analytics MCP.
---

# /youtube analyze

## Research Foundation
- **YouTube Analytics API**: 200-result limit per query; use Reporting API for bulk 60-day exports
- **Demand Curve, 2025**: Tutorial channels — 80% of subscribers come from <20% of videos (power law distribution)
- **Focus Digital, Dec 2025**: Tutorial channel CTR benchmarks: Poor <3%, Avg 3–5%, Good 5–8%, Excellent >8%
- **vidIQ cadence data**: Channels posting 2–3x/week grow subscribers 4x faster than 1x/week
- **Briggsby, 2024**: Videos >7 minutes rank higher for competitive keywords; tutorial sweet spot 8–15 min

## Data to Pull (auto)

```
get_analytics(last 90 days) — views, watchTime, subs, impressions, CTR
get_top_videos(last 90 days) — by views, by subs gained
get_traffic_sources(last 90 days) — YouTube Search %, Browse %, Suggested %, External %
get_audience_demographics(last 90 days) — age, gender, country
get_low_ctr_videos() — worst performers for action
get_channel_overview() — baseline stats
```

## Analysis Framework

### LAYER 1 — Funnel Health
```
Impressions → Views (CTR) → Watch Time → Subscribers
     ↑              ↑              ↑              ↑
  Thumbnail    Title + Hook    Script/Content   CTA + Value
```

Diagnose at which layer the funnel breaks:
- **CTR <3%**: Thumbnail or title problem — not a content problem
- **CTR good but low watch time**: Hook or first 30s losing people
- **Watch time good but low subs**: Missing CTA, wrong audience, or value not unique enough
- **Subs good but low views lately**: Upload cadence dropped, or algorithm deprioritised channel

### LAYER 2 — Traffic Source Health

| Source | Healthy % | Warning | Problem |
|--------|-----------|---------|---------|
| YouTube Search | 30–50% | 20–30% | <20% |
| Browse/Home | 20–35% | 10–20% | <10% |
| Suggested Videos | 15–30% | 5–15% | <5% |
| External | 5–15% | — | >40% (over-reliant on external) |
| Shorts Feed | Growing | Flat | 0% (not posting Shorts) |

**Key insight**: If YouTube Search % is low, SEO is the problem. If Suggested % is low, watch time signals are weak (algorithm won't recommend). If Browse % is low, subscriber engagement is low.

### LAYER 3 — Content Performance Pattern
Identify: which video types perform above average vs below.
- Compare widget-specific vs broad Elementor tutorials
- Compare video lengths (under 8 min vs 8–15 min vs 15+ min)
- Compare publish day/time patterns
- Identify the "power law" videos (top 20% driving 80% of growth)

### LAYER 4 — Subscriber Conversion Health

**Target ratios (tutorial/WordPress niche):**
- Sub/view ratio: 0.3–1% = healthy, >1% = excellent, <0.1% = broken
- Days to first 100 subs on new video: <7 days = strong, >30 days = weak SEO
- Returning viewer %: >30% = good audience loyalty

**If sub/view ratio is broken (<0.1%):**
Root causes to check:
1. No subscribe CTA in video (add at 25% mark)
2. Subscribe link without `?sub_confirmation=1`
3. Audience is landing but doesn't see value in more content (mismatch)
4. Channel art/description doesn't communicate the ongoing value

## Output Format

```
# CHANNEL ANALYTICS REPORT
Period: [date range]
Data pulled: [timestamp]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## FUNNEL SCORECARD

| Stage | Metric | Your Channel | Benchmark | Grade |
|-------|--------|-------------|-----------|-------|
| Impressions→Views | CTR | [X]% | 4–8% | [A-F] |
| Views→Watch Time | Avg Duration | [X]% | 35–50% | [A-F] |
| Watch Time→Subs | Sub/View | [X]% | 0.3–1% | [A-F] |
| Overall funnel | Efficiency | [score] | — | [A-F] |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## TRAFFIC SOURCES
[Breakdown table with health status]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## TOP PERFORMING VIDEOS (last 90 days)
[Table: title, views, CTR, subs gained]

## LOWEST PERFORMING (opportunity list)
[Table: title, views, age, what's wrong]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## ROOT CAUSE DIAGNOSIS
[2-3 sentences on the #1 bottleneck]

## PRIORITY ACTIONS (by impact)
1. [Highest impact action + specific instruction]
2. [Action]
3. [Action]
4. [Action]
5. [Action]

## 30-DAY PROJECTION (if actions completed)
Views: [current monthly] → [projected]
Subs/month: [current] → [projected]
CTR: [current]% → [projected]%
```
