# Claude Setup Guide

Connect the Google Meta Ads GA4 MCP server to Claude Desktop, Claude Code, or Gemini CLI.

---

## Claude Desktop

### Step 1: Open Configuration

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

If the file doesn't exist, create it.

### Step 2: Add the MCP Server

Paste this into your config file:

```json
{
  "mcpServers": {
    "google-meta-ads-ga4": {
      "url": "YOUR_MCP_ENDPOINT_URL"
    }
  }
}
```

> If you already have other MCP servers configured, add `"google-meta-ads-ga4"` as a new key inside the existing `"mcpServers"` object.

### Step 3: Restart Claude Desktop

Close and reopen Claude Desktop. You should see the MCP tools icon (hammer) in the chat input area.

### Step 4: Verify Connection

Type this in Claude:

```
List all my Google Ads accounts
```

If connected correctly, Claude will use the `list_accounts` tool and show your accounts.

---

## Claude Code

### Quick Setup

```bash
claude mcp add google-meta-ads-ga4 --transport sse YOUR_MCP_ENDPOINT_URL
```

### Verify

```bash
claude mcp list
```

You should see `google-meta-ads-ga4` in the list.

---

## Gemini CLI

### Install as Extension

```bash
gemini extensions install google-meta-ads-ga4 --url YOUR_MCP_ENDPOINT_URL
```

### Verify

```bash
gemini extensions list
```

---

## Troubleshooting

### MCP tools not showing up

1. Make sure the config JSON is valid (no trailing commas)
2. Restart the application completely
3. Check that the MCP endpoint URL is correct and accessible

### Authentication errors

1. The server uses OAuth — you'll be prompted to connect your Google/Meta accounts on first use
2. Make sure pop-ups are not blocked when the OAuth window opens
3. Try disconnecting and reconnecting your account

### "Tool not found" errors

Make sure you're using the correct tool names. Google Ads tools use their original names (e.g., `list_accounts`), Meta tools are prefixed with `meta_` (e.g., `meta_get_campaigns`), and GA4 tools are prefixed with `ga_` (e.g., `ga_run_report`).

---

## Important Usage Notes

1. **Google Ads:** Always call `list_accounts` first before using any other Google Ads tools
2. **Meta Ads:** Always call `meta_get_ad_accounts` first to get your Meta ad account IDs (they start with `act_`)
3. **GA4:** Call `ga_get_account_summaries` first to see available properties
4. **Keyword data:** Always use `keyword_planner` for volume data — never guess keyword metrics
