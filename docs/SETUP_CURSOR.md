# Cursor & Cline Setup Guide

Connect the Google Meta Ads GA4 MCP server to Cursor IDE or Cline.

---

## Cursor

### Step 1: Open MCP Configuration

Create or edit `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "google-meta-ads-ga4": {
      "url": "YOUR_MCP_ENDPOINT_URL"
    }
  }
}
```

### Step 2: Restart Cursor

Close and reopen Cursor. The MCP tools will be available in the AI chat panel.

### Step 3: Verify

In Cursor's AI chat, type:

```
List my Google Ads accounts using the list_accounts tool
```

---

## Cline

### Step 1: Open Cline Settings

1. Open VS Code with Cline extension installed
2. Open Cline settings (gear icon in the Cline panel)
3. Navigate to **MCP Servers**

### Step 2: Add Server

Add the following configuration:

```json
{
  "google-meta-ads-ga4": {
    "url": "YOUR_MCP_ENDPOINT_URL"
  }
}
```

### Step 3: Verify

Ask Cline:

```
Use the list_accounts tool to show my Google Ads accounts
```

---

## Use Cases for Cursor/Cline

While primarily code editors, these tools are great for:

- **Building ad dashboards** — Query live ad data while writing dashboard code
- **Generating reports** — Pull metrics directly into your development workflow
- **Automation scripts** — Test API calls interactively before writing automation code
- **Data analysis** — Combine ad data with your application's analytics code
