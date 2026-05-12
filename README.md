# BrightSite MCP Server

The official [Model Context Protocol](https://modelcontextprotocol.io) server for [BrightSite](https://onbrightsite.com) — connect AI assistants like Claude to manage your websites, pages, blog posts, components, forms, media, and analytics.

## Endpoint

```
https://onbrightsite.com/api/mcp
```

Transport: **Streamable HTTP**.

## Authentication

The server supports two authentication methods. Most modern MCP clients will negotiate OAuth automatically; clients that don't can fall back to a Bearer token.

### OAuth 2.1 (recommended)

OAuth-capable clients (Claude.ai, ChatGPT, Claude Desktop with OAuth, etc.) discover the auth flow automatically via [`/.well-known/oauth-protected-resource`](https://onbrightsite.com/.well-known/oauth-protected-resource). Dynamic Client Registration (RFC 7591) is supported — no manual app setup needed.

### Bearer token

For clients that don't support OAuth, generate a personal API key:

1. Sign in at [onbrightsite.com](https://onbrightsite.com)
2. Go to **Settings → MCP Keys**
3. Create a new key (format: `bs_...`)
4. Configure your client with:

```json
{
  "mcpServers": {
    "brightsite": {
      "url": "https://onbrightsite.com/api/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

## Capabilities

- **Pages** — create, update, publish, duplicate; manage layouts, HEEx templates, and SEO metadata
- **Blog** — posts, listing/post-card designs, blog settings, templates
- **Components** — reusable UI blocks with editable props
- **Forms** — create forms, view submissions
- **Media** — upload files, manage folders
- **Analytics** — visitor stats, top pages, referrers, device/browser/country breakdowns
- **Redirects, layouts, error pages, global code, versioning**

## Registry

This server is published to the [MCP Registry](https://registry.modelcontextprotocol.io) as `io.github.brightsitehq/brightsite`. The canonical metadata is in [`server.json`](./server.json).

## Links

- Website: <https://onbrightsite.com>
- Sign up: <https://onbrightsite.com>
- MCP spec: <https://modelcontextprotocol.io>
