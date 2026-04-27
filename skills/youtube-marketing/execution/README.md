# Execution Scripts

This folder is for helper scripts that support the skill suite.

The MCP server (`server.js` at repo root) handles live YouTube API operations:
- Reading channel analytics
- Fetching video metadata
- Pushing SEO updates

## Planned Scripts

| Script | Purpose | Status |
|--------|---------|--------|
| `fetch_channel_data.js` | Pull channel stats snapshot | Planned |
| `fetch_video_analytics.js` | Export video performance CSV | Planned |
| `search_competitor_videos.js` | SERP snapshot for a keyword | Planned |
| `bulk_export_metadata.js` | Export all video titles/descriptions | Planned |

## Contributing a Script

- Node.js preferred (matches the rest of the codebase)
- Must have a CLI interface: `node script.js --flag value`
- Document required environment variables
- No hardcoded credentials — use `.env` or pass as args
