# YouTube MCP Server + Marketing Skills

**Connect any AI agent to your YouTube channel — then give it 21 marketing commands.**

One repo. Two layers:
- **MCP Server** — 10 tools that read your real channel data and push updates directly to YouTube
- **21 Skill Commands** — SEO, scripts, analytics, Shorts, batch updates, WordPress publishing, and funnel analysis

[![npm version](https://img.shields.io/npm/v/youtube-channel-mcp?style=for-the-badge&color=CB3837&logo=npm)](https://www.npmjs.com/package/youtube-channel-mcp)
[![npm downloads](https://img.shields.io/npm/dm/youtube-channel-mcp?style=for-the-badge&color=CB3837&logo=npm)](https://www.npmjs.com/package/youtube-channel-mcp)
[![GitHub Stars](https://img.shields.io/github/stars/adityaarsharma/youtube-mcp-server?style=for-the-badge&logo=github)](https://github.com/adityaarsharma/youtube-mcp-server)
[![License MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Claude MCP](https://img.shields.io/badge/Claude-MCP%20Server-FF6B35?style=for-the-badge&logo=anthropic)](https://claude.ai)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-43853D?style=for-the-badge&logo=node.js)](https://nodejs.org)

---

## Works With

| Agent | Via | Status |
|-------|-----|--------|
| Claude Code | Skill files + MCP | ✅ Full support |
| Claude Desktop | MCP server | ✅ Full support |
| Cursor | MCP server | ✅ Full support |
| Windsurf | MCP server | ✅ Full support |
| OpenAI Codex | Skill files | ✅ Full support |
| Gemini CLI | Skill files | ✅ Full support |
| Any MCP client | Remote HTTP/SSE | ✅ Full support |

---

## Why This Exists

VidIQ gives you a score. TubeBuddy gives you a checklist.

Neither of them can **push an update to your video**, **write a retention-engineered script**, or **publish a companion blog post to WordPress** — all in one workflow.

```
/youtube ideate       → 10 ranked ideas + live keyword data
/youtube seo          → 3 title variants + full description + 20 tags
/youtube script       → retention-engineered tutorial script
/youtube metadata     → copy-paste upload package, pushed to YouTube via MCP
/youtube batch-seo    → bulk-update worst-performing videos sorted by CTR
/youtube wp-post      → companion blog post → WordPress REST API publish
```

**No other tool does the YouTube → WordPress publishing pipeline.**
**No other tool is aware you're a product company, not an ad-revenue creator.**

---

## MCP Server — 10 Tools

Live read/write access to your YouTube channel via OAuth2.

```
Claude  →  YouTube MCP Server  →  YouTube APIs  →  Your Channel
(you)        (this repo)           (OAuth2)         (stays local)
```

Everything runs on your machine. Nothing sent to third parties.

| Tool | What It Does |
|------|-------------|
| `get_video_details` | Full metadata — title, description, tags, privacy status, stats, duration |
| `search_my_videos` | Search your channel by keyword — returns metadata + stats |
| `update_video_seo` | Push title, description, tags directly to YouTube |
| `get_channel_overview` | Subscribers, total views, video count |
| `get_all_videos` | All videos with stats, sorted by date or views |
| `get_analytics_over_time` | Day-by-day views, watch time, subscribers for any date range |
| `get_top_videos_analytics` | Top videos ranked by views — with retention %, subs gained |
| `get_audience_demographics` | Countries, device types, age groups, gender |
| `get_traffic_sources` | Search, Suggested, Browse, External — with percentages |
| `analyze_and_suggest_topics` | AI-powered topic analysis from your channel data |

---

## 21 Skill Commands

| Command | What It Does |
|---------|-------------|
| `/youtube seo` | 3 title variants, description, 20 tags — with live keyword data |
| `/youtube audit` | 4-dimension channel health audit with A–F grades |
| `/youtube script` | Retention-engineered tutorial script, pattern interrupts every 60–90s |
| `/youtube hook` | 5 hook variants with drop-off risk ratings |
| `/youtube thumbnail` | 3 A/B thumbnail briefs with full design specs |
| `/youtube ideate` | 10 ranked video ideas with keyword volume + SERP gap |
| `/youtube analyze` | Analytics diagnosis — CTR, retention, traffic sources, sub conversion |
| `/youtube calendar` | Monthly content plan with Shorts supplement + upload cadence |
| `/youtube shorts` | Vertical-format Short: script, metadata, visual markers |
| `/youtube repurpose` | 7-platform expansion: Shorts, blog, LinkedIn, X, email, podcast, Community |
| `/youtube competitor` | Keyword gaps, format gaps, SERP map using live data |
| `/youtube metadata` | Copy-paste upload package with pre-publish checklist |
| `/youtube strategy` | Channel positioning, content pillars, 30/60/90-day milestones |
| `/youtube wp-post` | Companion blog post → WordPress publish + VideoObject schema |
| `/youtube plugin-demo` | Script + SEO template for software/plugin demo videos |
| `/youtube batch-seo` | Bulk SEO update for lowest-performing videos |
| `/youtube funnel` | Video → landing page → product purchase funnel map |
| `/youtube comment-intel` | Mine comments for feature requests, pain points, reply templates |
| `/youtube shorts-from-long` | Extract 3–5 Shorts from any existing long-form video |
| `/youtube collab` | Channel collab opportunity finder for your niche |
| `/youtube monetize` | Revenue strategy across 7 streams |

---

## Skill File Structure

```
skills/youtube-marketing/
  SKILL.md              ← entry point, routing, channel config
  sub-skills/           ← 21 command instruction files
  references/           ← 9 on-demand knowledge guides (data-cited)
  templates/            ← 6 channel type configs
  execution/            ← helper scripts
references/
  whitepapers.md        ← full citation database
```

---

## Setup

**Prerequisites:** Node.js 18+, Google Cloud project with YouTube Data API v3 + YouTube Analytics API enabled, OAuth 2.0 credentials (Desktop app type).

### Option A — npx (Zero Install)

```bash
npx youtube-channel-mcp
```

### Option B — Clone + Run

```bash
git clone https://github.com/adityaarsharma/youtube-mcp-server
cd youtube-mcp-server
npm install
```

Or use the install script:

```bash
curl -fsSL https://raw.githubusercontent.com/adityaarsharma/youtube-mcp-server/main/install.sh | bash
```

### Authenticate

```bash
node auth.js
```

Opens a browser for OAuth. Saves `tokens.json` locally. Grants full read + write scopes including `youtube.force-ssl`.

### Add to Claude Code

```json
{
  "mcpServers": {
    "youtube-marketing": {
      "command": "node",
      "args": ["/path/to/youtube-mcp-server/server.js"]
    }
  }
}
```

### Add to Claude Desktop

```json
{
  "mcpServers": {
    "youtube-marketing": {
      "command": "npx",
      "args": ["youtube-channel-mcp"]
    }
  }
}
```

### Remote Mode — Team Access (HTTP/SSE)

```bash
MODE=remote PORT=3001 node server.js
```

```json
{
  "mcpServers": {
    "youtube-marketing": {
      "type": "sse",
      "url": "https://your-server.com:3001/sse"
    }
  }
}
```

### Install Skill Files

```json
{
  "skills": ["/path/to/youtube-mcp-server/skills/youtube-marketing/SKILL.md"]
}
```

---

## Configure for Your Channel

Open `skills/youtube-marketing/SKILL.md` and set your channel constants once:

```markdown
## Channel Profile — [Your Channel]

- Subscribers: [N] | Videos: [N] | Avg daily views: [N]
- Best publish time: [your timezone]
- Products: [your products]
- Discount code: [your code]
- Fixed links in every description: [your links]
```

Every command now knows your channel's products, pricing, conversion goals, and audience. It writes descriptions with your links, recommends titles for your niche, and diagnoses your funnel — not a generic creator's.

**Choose your channel type** from `skills/youtube-marketing/templates/`:

| Template | For |
|----------|-----|
| `product-company.md` | Plugin/SaaS companies (POSIMYTH default) |
| `tutorial-channel.md` | Pure tutorial, affiliate revenue |
| `personal-brand.md` | Consulting/coaching funnel |
| `saas-channel.md` | Trial signups |
| `wordpress-specialist.md` | WP ecosystem, affiliate |
| `agency-channel.md` | Client acquisition |

---

## Research Foundation

Every recommendation is grounded in published data:

| Source | Finding |
|--------|---------|
| Retention Rabbit (150M+ minutes) | Hook length 28–42s optimal for tutorials |
| Wistia, 2024 | Pattern interrupts every 60–90s → −40% drop-off |
| Focus Digital, Dec 2025 | Tutorial CTR benchmarks: Poor <3%, Avg 3–5%, Good 5–8%, Excellent >8% |
| vidIQ (5M channel dataset) | 2–3x/week upload cadence → 4x subscriber growth |
| vidIQ (5M channel dataset) | Face in thumbnail → +38% CTR |
| BrightEdge, 2025 | Blog post with YouTube embed ranks 53% higher on Google |
| Yoast SEO Study, 2024 | VideoObject schema on WordPress → +31% Google CTR |
| ConversionXL, 2024 | Plugin demo videos convert at 2.8–6% |
| YouTube Official, Sept 2025 | Shorts freshness decay: 28–30 day cliff |
| HubSpot, 2024 | Content repurposed to 3+ formats → 3.5x total reach |

Full citations: [`references/whitepapers.md`](references/whitepapers.md)

---

## Compatible Integrations

| Integration | Used For |
|-------------|---------|
| **DataForSEO MCP** | Keyword research, live SERP analysis |
| **WordPress MCP** | Publishing companion posts via `/youtube wp-post` |
| **Google Search Console MCP** | Cross-referencing search performance |
| **GA4 MCP** | Traffic attribution in `/youtube funnel` |
| **Figma MCP** | Thumbnail brief → design handoff |

---

## License

MIT — [Aditya Sharma](https://adityaarsharma.com)
