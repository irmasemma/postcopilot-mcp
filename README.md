# PostCopilot — Threads MCP server

**Export any public Threads profile's posts, followers and following straight into Claude — no login, no OAuth, no API key, no browser extension.**

PostCopilot is a hosted [Model Context Protocol](https://modelcontextprotocol.io) server for [Threads](https://www.threads.com). You add one URL to your MCP client (Claude, Cursor, or any MCP app) and get tools that export a **public** profile's data and return the rows right in the chat. The export runs entirely on PostCopilot's servers — you never log into Threads and never run anything locally.

## Why it's different

Every other Threads MCP server wraps Meta's official Graph API, so it's OAuth-walled to **your own** account and can only read what Meta exposes. PostCopilot is the only one that exports **any public profile's** followers, following and posts with **no login at all** — the practical "Threads data API for AI."

## Quick start (free, no sign-in)

Add this remote MCP server to your client — in Claude: **Settings → Connectors → Add custom connector**, leave auth empty:

```
https://postcopilot.ai/mcp
```

That's it. The free public endpoint allows **2 exports per day per IP**. Then ask, e.g.:

> "Export @zuck's followers."
> "Get the 20 most recent posts from https://www.threads.com/@mosseri."
> "Download the video from this Threads post: …"

## Tools

| Tool | What it does | Free limit |
|------|--------------|-----------|
| `postcopilot_export_profile` | Export a profile's recent posts (text, likes, replies, reposts, timestamps) | 20 posts |
| `postcopilot_export_followers` | Export a profile's followers (usernames + profile URLs) | 60 |
| `postcopilot_export_following` | Export who a profile follows | 60 |
| `postcopilot_download_video` | Direct, watermark-free video download URLs from a Threads post | — |
| `postcopilot_generate_post` | Generate a Threads caption with a fine-tuned model | — |
| `postcopilot_read_guide` | Read PostCopilot's Threads guides/blog | — |

All tools take a public Threads profile or post URL (e.g. `https://www.threads.com/@username`).

## Higher limits (optional)

For larger exports (up to 2,000 rows per profile, a 24-hour result buffer, and `list_exports` / `get_export` / `query_export` to read and filter results server-side), mint a personal connector URL on the connector page:

**https://postcopilot.ai/threads-mcp-connector**

- **Free** — the public endpoint above (2 exports/day).
- **$2 day pass** or **$39.99/mo Queue Pro** — a personal `pcb_…` connector URL with the higher caps.

## Links

- Connector page & setup: https://postcopilot.ai/threads-mcp-connector
- Website: https://postcopilot.ai

## License

MIT — see [LICENSE](./LICENSE). This repo contains the public manifest and documentation for the hosted PostCopilot MCP server; the server itself is hosted at `https://postcopilot.ai/mcp`.
