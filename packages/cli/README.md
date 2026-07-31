# vibedrop

Deploy static sites from your agent in one command.

## Install

```bash
npx @vibedrop/cli deploy ./dist
```

First run auto-provisions an anonymous API key to `~/.vibedrop/config.json`. No signup required.

## Commands

```bash
vibedrop deploy <dir>       Deploy a directory (link-only by default)
  --public                  Submit to Explore and allow indexing
  --unlisted                Keep an existing site link-only
  --password <password>     Password-protect a site (Pro)
vibedrop claim-url           Generate a fresh one-time claim URL
vibedrop list                List your deployed sites
vibedrop rm <slug>           Delete a site
vibedrop whoami              Show current API key + server
```

## Free tier

- Rolling 30-day inactivity window for link-only sites
- Public, moderated sites remain available without an expiry
- 25 MB max per site
- 20 active sites
- Small footer banner

Upgrade to Pro at [vibedrop.cc/#pricing](https://vibedrop.cc/#pricing) for permanent link-only sites, 50 MB per site, 200 sites, password protection, and optional branding.

## MCP server

Also available as an MCP server for Claude Code, Cursor, Windsurf:

```bash
npm install -g @vibedrop/mcp
```

See [@vibedrop/mcp](https://www.npmjs.com/package/@vibedrop/mcp).
