# n8n Setup Guide

Connect the Google Meta Ads GA4 MCP server to n8n for workflow automation.

---

## Overview

n8n supports MCP servers via the **MCP Client Tool** node using Streamable HTTP. This lets you build automated workflows that manage your Google Ads, Meta Ads, and GA4 data.

---

## Quick Start

### Option 1: Import Workflow Template

1. Open n8n
2. Click **Import from file**
3. Select [`configs/n8n_workflow.json`](../configs/n8n_workflow.json) from this repository
4. Update the MCP endpoint URL in the MCP Client node
5. Activate the workflow

### Option 2: Build from Scratch

#### Step 1: Add MCP Client Tool Node

1. Create a new workflow
2. Add an **MCP Client Tool** node
3. Configure:
   - **Server URL:** `YOUR_MCP_ENDPOINT_URL`
   - **Transport:** Streamable HTTP
   - **Authentication:** Bearer (recommended) or None

#### Step 2: Connect to an AI Agent

1. Add an **AI Agent** node
2. Connect the MCP Client Tool as a tool input to the AI Agent
3. Configure the AI Agent with your preferred LLM (GPT-4, Claude, etc.)

#### Step 3: Add a Trigger

Choose how to trigger your workflow:
- **Schedule Trigger** — Run on a cron schedule (e.g., daily reports)
- **Webhook Trigger** — Trigger via HTTP request
- **Manual Trigger** — Run on demand

---

## Example Workflows

### Daily Campaign Report

```
Schedule (9am daily)
  → AI Agent: "Get yesterday's performance for all active Google Ads 
    and Meta Ads campaigns. Summarize spend, clicks, conversions, and ROAS."
  → Send results to Slack/Email
```

### Budget Alert Monitor

```
Schedule (every hour)
  → AI Agent: "Check if any campaign has spent more than 80% of its 
    daily budget. List campaigns approaching their budget limit."
  → IF over threshold → Send Slack alert
```

### Weekly Cross-Platform Report

```
Schedule (Monday 8am)
  → AI Agent: "Compare Google Ads vs Meta Ads performance for last week.
    Include spend, conversions, CPA, and ROAS for each platform.
    Also pull GA4 data for total website conversions."
  → Format as HTML → Send email to team
```

### Auto-Pause Underperformers

```
Schedule (daily)
  → AI Agent: "Find all Google Ads campaigns with ROAS below 1.0 
    in the last 7 days and pause them."
  → Log results to Google Sheets
```

---

## Authentication & Security

### Bearer Token (Recommended)

1. In the MCP Client node, set **Authentication** to **Bearer**
2. Enter your bearer token
3. This prevents unauthorized access to your MCP endpoint

### Network Security

- If running n8n self-hosted, ensure your instance can reach the MCP endpoint URL
- For n8n Cloud, no additional network configuration is needed
- Consider using n8n's credential encryption for storing tokens

---

## Tips

- **Batch operations:** Use the batch tools (`add_batch_campaign_operations`, `meta_batch_update_catalog_products`) for bulk changes
- **Error handling:** Add error handler nodes after the AI Agent to catch API failures
- **Rate limits:** Add wait nodes between API-heavy operations to avoid rate limiting
- **Logging:** Use the n8n execution log to debug MCP tool calls

---

## Troubleshooting

### MCP connection timeout

- Verify the endpoint URL is correct
- Check that n8n can reach the URL (no firewall blocking)
- If self-hosted, ensure you're running a single webhook replica for MCP (SSE requires sticky sessions)

### Tools not appearing

- The MCP Client node auto-discovers available tools
- Try disconnecting and reconnecting the MCP server
- Check the n8n execution log for error details

### Authentication errors

- Ensure the bearer token is correct
- The OAuth flow will be triggered on first use for Google/Meta accounts
