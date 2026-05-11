# YouTube Marketing Skills

**Build a YouTube personal brand with live channel data, AI-generated SEO, and organic-only growth strategy — no paid ads, no $99/month subscription.**

[![npm version](https://img.shields.io/npm/v/youtube-channel-mcp?style=for-the-badge&color=CB3837&logo=npm)](https://www.npmjs.com/package/youtube-channel-mcp)
[![npm downloads](https://img.shields.io/npm/dm/youtube-channel-mcp?style=for-the-badge&color=CB3837&logo=npm)](https://www.npmjs.com/package/youtube-channel-mcp)
[![GitHub Stars](https://img.shields.io/github/stars/adityaarsharma/youtube-marketing-skills?style=for-the-badge&logo=github)](https://github.com/adityaarsharma/youtube-marketing-skills)
[![License MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-43853D?style=for-the-badge&logo=node.js)](https://nodejs.org)

21 commands · 10 live channel tools · Works with Claude Code, Cursor, Codex, Gemini CLI · MIT

---

**If this grows your channel — [⭐ star this repo](https://github.com/adityaarsharma/youtube-marketing-skills).** It's the only signal that tells us what to build next.

---

## What This Is

A Claude Code skill suite + MCP server that connects your AI to your **real YouTube channel** — reads your private analytics, writes SEO back to YouTube, and publishes companion posts to WordPress. Not a generic creator template. Not another dashboard.

**Three things no other YouTube AI tool does:**

1. **Reads your private analytics** via OAuth — watch time, retention %, traffic sources, demographics. Not just public stats anyone can scrape.
2. **Writes back to YouTube** — pushes updated titles, descriptions, and tags directly from Claude. No opening YouTube Studio.
3. **Double-ranks on Google** — publishes a companion WordPress post with VideoObject schema so the same topic ranks on both Google and YouTube simultaneously.

```
/youtube-ideate  →  /youtube-script  →  /youtube-seo  →  push to YouTube
                                                        ↓
                                         /youtube-wp-post  →  published to WordPress
```

---

## Who This Is For

Built for **developers, consultants, and product makers** who use YouTube to build authority — not entertainment creators chasing trending content.

- You make tutorials, walkthroughs, or educational content in your niche
- You want **organic-only growth** — no paid ads, no bought subscribers, no gaming the system
- You have a product, service, open-source project, or community to grow through video
- You want **evergreen content** — videos that get discovered for years, not just 48 hours after upload

One subscriber from your niche is worth more than 10,000 random views. This tool understands that.

---

## Quick Start

**Prerequisites:** Node.js 18+, Google Cloud project with YouTube Data API v3 + YouTube Analytics API enabled, OAuth 2.0 Desktop credentials.

```bash
# 1. Install
npx youtube-channel-mcp

# 2. Authenticate once — opens browser, saves tokens locally on your machine
node auth.js
```

Add to Claude Code `settings.json`:

```json
{
  "mcpServers": {
    "youtube": {
      "command": "npx",
      "args": ["youtube-channel-mcp"]
    }
  },
  "skills": ["/path/to/youtube-marketing-skills/skills/youtube-marketing/SKILL.md"]
}
```

Configure your channel once — open `skills/youtube-marketing/SKILL.md` and set:

```markdown
Channel: [Your channel name and handle]
Products: [Your products with URLs]
Best publish time: [Your optimal time + timezone]
Fixed links: [Product / docs / community URLs to embed in every description]
```

Every command now knows your business. Start with:

```
/youtube-ideate
```

---

## 21 Commands

### Strategy & Planning

| Command | What It Does |
|---------|-------------|
| `/youtube-strategy` | Channel positioning, content pillars, 30/60/90-day growth milestones |
| `/youtube-ideate` | 10 ranked video ideas with live keyword volume + SERP gap analysis |
| `/youtube-calendar` | Monthly content plan with Shorts supplement + upload cadence |
| `/youtube-competitor` | Keyword gaps, format gaps, live SERP map of your niche |

### Production

| Command | What It Does |
|---------|-------------|
| `/youtube-script` | Retention-engineered tutorial script, pattern interrupts every 60–90s |
| `/youtube-hook` | 5 hook variants with drop-off risk ratings |
| `/youtube-thumbnail` | 3 A/B thumbnail briefs with full design specs and CTR predictions |
| `/youtube-shorts` | Vertical-format Short: script, metadata, visual markers |

### SEO & Upload

| Command | What It Does |
|---------|-------------|
| `/youtube-seo` | 3 title variants, full description, 20 ordered tags — grounded in live keyword data |
| `/youtube-metadata` | Copy-paste upload package with pre-publish checklist |
| `/youtube-wp-post` | Companion blog post → WordPress publish + VideoObject schema |
| `/youtube-plugin-demo` | Script + SEO template for software demo and tutorial videos |

### Analytics & Optimization

| Command | What It Does |
|---------|-------------|
| `/youtube-audit` | 4-dimension channel health audit with A–F grades |
| `/youtube-analyze` | CTR, retention, traffic sources, sub conversion — diagnosis + priority actions |
| `/youtube-batch-seo` | Bulk SEO update across your lowest-performing videos, auto-pushed to YouTube |
| `/youtube-comment-intel` | Mine comments for feature requests, pain points, reply templates |

### Growth & Expansion

| Command | What It Does |
|---------|-------------|
| `/youtube-repurpose` | 7-platform expansion: Shorts, blog, LinkedIn, X, email, podcast, Community post |
| `/youtube-shorts-from-long` | Extract 3–5 Shorts from any existing long-form video |
| `/youtube-funnel` | Video → landing page → product purchase funnel map |
| `/youtube-collab` | Collaboration opportunity finder — channels to partner with in your niche |
| `/youtube-monetize` | Revenue strategy across 7 streams |

---

## Live Channel Tools

What makes this different from every other Claude YouTube skill: **it connects to your real channel.**

Direct read/write via OAuth2. Runs entirely on your machine — your data never leaves your computer.

| Tool | What It Does |
|------|-------------|
| `get_video_details` | Full metadata — title, description, tags, privacy status, stats |
| `search_my_videos` | Search your own channel by keyword |
| `update_video_seo` | Push title, description, tags directly to YouTube |
| `get_channel_overview` | Subscribers, total views, video count |
| `get_all_videos` | All videos with stats, sorted by date or views |
| `get_analytics_over_time` | Day-by-day views, watch time, subscribers for any date range |
| `get_top_videos_analytics` | Top videos by views — with retention %, subs gained |
| `get_audience_demographics` | Countries, device types, age groups, gender |
| `get_traffic_sources` | Search, Suggested, Browse, External — with percentages |
| `analyze_and_suggest_topics` | Channel data → AI-powered gap analysis and topic suggestions |

---

## The Organic Growth Playbook

No ads. No paid promotion. No viral luck. This is how personal brands compound on YouTube.

### 1. Find Evergreen Gaps

Evergreen content = keywords with consistent monthly search volume, not trending spikes that collapse in a week.

`/youtube-ideate` pulls live keyword data and surfaces gaps: real searches with volume that your competitors aren't targeting yet.

**What to look for:** Keywords where the top-ranking videos are 12+ months old, have weak titles, or come from channels outside your niche. That's unclaimed territory.

### 2. One Video, Three Discovery Paths

Every video you make should be built to win across three separate discovery systems:

- **YouTube Search** — title + description + tags targeting one specific query
- **Google Search** — companion WordPress post with VideoObject schema (same topic, two rankings)
- **Suggested** — thumbnail + hook optimized for your existing subscriber cohort

`/youtube-seo` + `/youtube-wp-post` handles all three in one workflow.

### 3. The Compounding Loop

```
Month 1:  Publish optimized tutorial → earns YouTube Search traffic
Month 2:  Companion post ranks on Google → new audience discovers the video
Month 3:  Video earns Suggested placement from a similar viewer cohort
Month 6:  Run /youtube-batch-seo → refresh titles with updated keyword data
Year 1:   This video drives 30–40% of your channel's total subscriber growth
```

`/youtube-batch-seo` automates the quarterly refresh. It finds your underperforming videos and pushes improved SEO — without you touching YouTube Studio.

### 4. Build a Gap Map, Not Just a Content Calendar

Most creators plan content by topic. Personal brands should plan by competitive gap.

```
/youtube-competitor  →  find what your niche isn't covering yet
/youtube-ideate      →  rank those gaps by keyword volume and competition score
/youtube-calendar    →  sequence by production effort and seasonal timing
```

This is the difference between a content calendar and a growth strategy.

---

## Channel Templates

Pick the template that fits your channel type — configure it once in `SKILL.md`:

| Template | Built For |
|----------|-----------|
| `personal-brand.md` | Consulting, coaching, courses, authority building |
| `product-company.md` | Plugin / SaaS / software companies |
| `tutorial-channel.md` | Pure tutorial — ad revenue + affiliates |
| `saas-channel.md` | Free trial → paid conversion funnel |
| `wordpress-specialist.md` | WordPress ecosystem, affiliate revenue |
| `agency-channel.md` | Client acquisition through authority content |

---

## Integrations

| Integration | What It Enables |
|-------------|----------------|
| **DataForSEO MCP** | Live keyword volume + SERP data in `/youtube-ideate` and `/youtube-seo` |
| **WordPress MCP** | Companion post publishing via `/youtube-wp-post` |
| **Google Search Console MCP** | Search performance cross-reference in `/youtube-analyze` |
| **GA4 MCP** | Traffic attribution in `/youtube-funnel` |
| **Figma MCP** | Thumbnail brief → design file handoff |
| **Slack MCP** | Batch SEO results + weekly analytics digests |

---

## Works With

| Agent | How |
|-------|-----|
| Claude Code | Skill files + live channel tools |
| Claude Desktop | Live channel tools via MCP |
| Cursor | Live channel tools via MCP |
| Windsurf | Live channel tools via MCP |
| OpenAI Codex | Skill files |
| Gemini CLI | Skill files |
| Any MCP client | Remote HTTP/SSE |

---

## Research Foundation

Every recommendation in every command is grounded in published data — not opinions.

| Source | Finding Used |
|--------|-------------|
| Retention Rabbit (150M+ minutes analyzed) | Hook length 28–42s is optimal for tutorials |
| Wistia, 2024 | Pattern interrupts every 60–90s → −40% drop-off |
| Focus Digital, Dec 2025 | CTR benchmarks: Poor <3%, Average 3–5%, Good 5–8%, Excellent >8% |
| vidIQ (5M channel dataset) | 2–3 uploads/week → 4x subscriber growth rate |
| vidIQ (5M channel dataset) | Face in thumbnail → +38% CTR |
| BrightEdge, 2025 | Blog post with YouTube embed → +53% Google ranking lift |
| Yoast SEO Study, 2024 | VideoObject schema on WordPress → +31% Google CTR |
| ConversionXL, 2024 | Software demo videos convert at 2.8–6% |
| YouTube Official, Sept 2025 | Shorts freshness decay: 28–30 day cliff |
| HubSpot, 2024 | Content repurposed to 3+ formats → 3.5x total reach |
| Demand Curve, 2025 | Top 20% of videos drive 80% of channel subscriber growth |
| Semrush, 2025 | WordPress tutorial queries spike Jan–Mar and Sep–Nov |

Full citations: [`references/whitepapers.md`](references/whitepapers.md)

---

## What's Inside

```
skills/youtube-marketing/
  SKILL.md          ← entry point — configure your channel once here
  sub-skills/       ← 21 command files
  references/       ← 9 knowledge guides (algorithm, analytics, SEO, Shorts, retention)
  templates/        ← 6 channel type configs
references/
  whitepapers.md    ← full citation database (14 published studies)
```

---

## vs. VidIQ / TubeBuddy

| VidIQ / TubeBuddy | YouTube Marketing Skills |
|-------------------|--------------------------|
| Suggests keywords | Pulls live SERP data + pushes the optimized title directly to YouTube |
| Shows a CTR score | Diagnoses why CTR is low + rewrites the thumbnail brief |
| Gives a tag list | Generates 20 prioritized tags + validates against YouTube policy |
| Dashboard only | Publishes a companion blog post to WordPress with VideoObject schema |
| One-size-fits-all | Learns your products, pricing, audience, and fixed links |
| No script help | Full retention-engineered script with pattern interrupts every 60–90s |
| $49–$99/month | Free. Open source. MIT. Runs entirely on your machine. |

---

## Other Install Options

```bash
# One-line shell script
curl -fsSL https://raw.githubusercontent.com/adityaarsharma/youtube-marketing-skills/main/install.sh | bash

# Clone and run
git clone https://github.com/adityaarsharma/youtube-marketing-skills
cd youtube-marketing-skills && npm install && node auth.js
```

**Remote mode** — share with a team:

```bash
MODE=remote PORT=3001 node server.js
```

---

## License

MIT — [Aditya Sharma](https://adityaarsharma.com)

---

*Built for channels where one subscriber is worth more than ten thousand ad views.*
