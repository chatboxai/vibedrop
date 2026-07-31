# @vibedrop/mcp

MCP server for deploying static sites to VibeDrop. Works with Claude Code, Cursor, Windsurf, and any MCP-compatible client.

## Quick Setup

### Claude Code

```bash
claude mcp add vibedrop -- npx @vibedrop/mcp
```

### Cursor

Add to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "vibedrop": {
      "command": "npx",
      "args": ["@vibedrop/mcp"]
    }
  }
}
```

### Windsurf / Other MCP clients

```json
{
  "command": "npx",
  "args": ["@vibedrop/mcp"]
}
```

## Tools

### `deploy_site`

Deploy a directory as a static website.

- `directory` (required): Absolute path to the directory containing index.html
- `slug` (optional): Existing site slug to redeploy at the same URL
- `title` (optional): Site title
- `visibility` (optional): `unlisted` (default) or `public`
- `password` (optional): Password protection for Pro sites; password sites are always unlisted

Returns a public URL like `https://abc123.vibedrop.site`.

### `deploy_html`

Deploy one HTML document directly without writing a directory first. Supports
the same `slug`, `title`, `visibility`, and `password` options. The body limit
is 16 MB.

### `claim_url`

Generate a fresh one-time URL that attaches the anonymous key and its sites to
a signed-in account.

### `list_sites`

List all deployed sites.

### `delete_site`

Delete a deployed site by slug.

## How it works

1. First call auto-provisions an anonymous API key (stored in `~/.vibedrop/config.json`)
2. Zips the directory, uploads to VibeDrop API
3. Returns a live URL anyone can visit
4. Free tier: rolling 30-day inactivity window for link-only sites, 25 MB max, 20 active sites
5. Public, moderated sites do not expire; Pro adds permanent link-only sites, 50 MB, 200 sites, password protection, and optional branding

## Environment Variables

- `VIBEDROP_API_URL`: Override API endpoint (default: `https://api.vibedrop.cc`)
