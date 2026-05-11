# Install Guide

Three ways to install. Pick what fits.

| Mode | Node.js? | OAuth Setup | Live Channel Data | Best For |
|------|----------|-------------|-------------------|----------|
| **1. Skill-Only** | No | No | No (paste data manually) | Trying it out, offline use |
| **2. Hosted MCP** | No | Yes (one-click via web) | Yes | Most people — no install hassle |
| **3. Local MCP** | Yes | Yes (local) | Yes | Privacy maximalists, advanced users |

**Privacy on Mode 2:** The hosted MCP is a stateless relay. **We don't store your YouTube data, your analytics, or your OAuth tokens.** Each request passes through with your token, hits YouTube's API, returns the response. Nothing is logged or persisted server-side.

---

## Mode 1 — Skill-Only (60 Seconds, No Install)

**What you get:** All 21 markdown commands. Claude generates SEO, scripts, ideas, audits — based on what you tell it about your channel. No live data access.

**What you don't get:** Reading your private analytics. Pushing SEO updates back to YouTube. Anything that needs OAuth.

### Claude Code

```bash
git clone https://github.com/adityaarsharma/youtube-marketing-skills.git
cp -r youtube-marketing-skills/skills/youtube-marketing ~/.claude/skills/
```

Open Claude Code, type `/youtube-strategy`. Done.

### Cursor / Windsurf / Codex / Gemini CLI

Drop the `skills/youtube-marketing/` folder into your agent's skills directory.

### Manual download (no git)

[Download ZIP](https://github.com/adityaarsharma/youtube-marketing-skills/archive/refs/heads/main.zip) → unzip → move `skills/youtube-marketing/` into `~/.claude/skills/`.

---

## Mode 2 — Hosted MCP (Recommended — No Node.js)

**What you get:** Everything Mode 1 gives you + live channel data + SEO write-back to YouTube. No software install required.

**How it works:**
1. You authorize YouTube via a one-click web flow → you get a refresh token
2. You paste the token into your Claude config along with the hosted MCP URL
3. Claude sends the token in each request → hosted MCP relays to YouTube → returns the data
4. Nothing is stored on our end. Tokens live only in your Claude config.

### Step 1 — Get Your YouTube Token

Open: **`https://youtube-skills.adityaarsharma.com/connect`** *(coming online once subdomain is live)*

Click **Connect YouTube** → log in with the Google account that owns your channel → grant permissions. The page displays your refresh token. Copy it.

### Step 2 — Add to Claude

**Claude Code** (`~/.claude/settings.json`):

```json
{
  "mcpServers": {
    "youtube": {
      "url": "https://youtube-mcp.adityaarsharma.com/sse",
      "transport": "sse",
      "env": {
        "YOUTUBE_REFRESH_TOKEN": "your-token-here"
      }
    }
  },
  "skills": ["~/.claude/skills/youtube-marketing/SKILL.md"]
}
```

**Claude Desktop**: same `mcpServers` block in `claude_desktop_config.json`.

**Cursor**: same block in `~/.cursor/mcp.json`.

### Step 3 — Add the Skill Files

Same as Mode 1 — clone repo, copy `skills/youtube-marketing/` to your skills directory. Skills are markdown, they live on your machine.

### Why Trust the Hosted MCP?

- **No data storage** — the server is stateless. No database, no logs of your tokens, no analytics on your channel data.
- **Open source** — the exact code running on the hosted endpoint is [in this repo](server.js). You can audit it.
- **Self-host fallback** — if you don't trust the hosted version, run the same code yourself with Mode 3. The hosted endpoint isn't doing anything special.

---

## Mode 3 — Local MCP (Full Control)

**What you get:** Everything Mode 2 gives you + everything runs on your machine. OAuth tokens never leave your computer.

**Requirements:**
- Node.js 18+ ([install](https://nodejs.org))
- Google Cloud project with **YouTube Data API v3** + **YouTube Analytics API** enabled
- OAuth 2.0 credentials, type "Desktop app" — saved as `credentials.json`

### Setup

```bash
# 1. Clone + install
git clone https://github.com/adityaarsharma/youtube-marketing-skills.git
cd youtube-marketing-skills && npm install

# 2. Put your credentials.json in this directory

# 3. Authenticate — opens browser, saves tokens locally
node auth.js
```

### Configure Claude

```json
{
  "mcpServers": {
    "youtube": {
      "command": "node",
      "args": ["/full/path/to/youtube-marketing-skills/server.js"]
    }
  },
  "skills": ["/full/path/to/youtube-marketing-skills/skills/youtube-marketing/SKILL.md"]
}
```

Or use npm:

```json
{
  "mcpServers": {
    "youtube": {
      "command": "npx",
      "args": ["youtube-channel-mcp"]
    }
  }
}
```

---

## Configure Your Channel (All Modes)

Open `skills/youtube-marketing/SKILL.md` (in your `~/.claude/skills/youtube-marketing/`) and set once:

```markdown
Channel: [Your channel name and handle]
Niche: [What you make videos about]
Products: [Your products with URLs]
Best publish time: [Day + time + timezone]
Fixed links: [URLs to embed in every description]
Discount code: [Your coupon, if any]
```

Every command now respects your config. For multi-brand setups, drop additional brand files in `templates/brands/` (that directory is gitignored — your private brand details stay local).

---

## Verify

```
# In Claude Code
/youtube-strategy
```

If Claude returns positioning + content pillars, you're good. If you're in Mode 2 or Mode 3, also try:

```
/youtube-audit
```

This pulls live channel data. If it works, your OAuth is wired correctly.

---

## Mode Comparison — When to Pick Which

**Pick Mode 1 (Skill-Only) if:**
- You're trying it out and don't want to set anything up
- You're on a locked-down machine where you can't install Node
- You're comfortable pasting analytics into Claude manually

**Pick Mode 2 (Hosted MCP) if:**
- You want live channel data without installing Node
- You don't want to set up a Google Cloud project
- You're OK with your YouTube API requests passing through a stateless relay you didn't build

**Pick Mode 3 (Local MCP) if:**
- You want zero third parties between Claude and YouTube
- You're already comfortable with Node + Google Cloud
- You're running this for a client / team and want full audit control

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| `node: command not found` | You're trying Mode 3 without Node. Use Mode 1 or 2 instead. |
| Claude says "skill not found" | Skills folder isn't in `~/.claude/skills/` — re-check the `cp -r` path |
| OAuth fails on Mode 2 connect page | Hosted endpoint may not be live yet — fall back to Mode 3 |
| `credentials.json not found` (Mode 3) | Download OAuth credentials from Google Cloud Console, save in package directory |
| API quota exceeded | YouTube Data API gives 10K units/day free; `/youtube-batch-seo` is expensive — run on smaller batches |
| Tokens expired (Mode 2/3) | Re-run the OAuth flow (`node auth.js` for Mode 3, refresh on hosted page for Mode 2) |

---

## What Gets Stored Where

| Data | Mode 1 | Mode 2 (Hosted) | Mode 3 (Local) |
|------|--------|-----------------|----------------|
| Skill markdown files | Your machine | Your machine | Your machine |
| Your YouTube channel data | Never accessed | Streamed through hosted MCP, not stored | Your machine |
| OAuth tokens | None | Your Claude config (not on our server) | `tokens.json` on your machine |
| Channel config (SKILL.md) | Your machine | Your machine | Your machine |
| API request logs | None | **None on our side** | None |
