# Windsurf Setup Guide

Connect the Google Meta Ads GA4 MCP server to Windsurf IDE.

---

## Setup

### Step 1: Open MCP Configuration

Create or edit `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "google-meta-ads-ga4": {
      "url": "YOUR_MCP_ENDPOINT_URL"
    }
  }
}
```

### Step 2: Restart Windsurf

Close and reopen Windsurf. The MCP tools will be available in the Cascade AI panel.

### Step 3: Verify

In Windsurf's Cascade chat, type:

```
List my Google Ads accounts
```

---

## Tips

- Use Windsurf's Cascade for multi-step ad management workflows
- Combine with code generation — build dashboards that pull live data
- Windsurf supports tool chaining, so you can say things like:
  ```
  Get my top 5 Google Ads campaigns by spend, then check their Meta Ads equivalents
  ```
