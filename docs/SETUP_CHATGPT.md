# ChatGPT Setup Guide

Connect the Google Meta Ads GA4 MCP server to ChatGPT.

---

## Prerequisites

- ChatGPT Plus, Team, or Enterprise subscription
- Access to ChatGPT's Connectors feature

---

## Setup Steps

### Step 1: Open Connectors

1. Open ChatGPT
2. Go to **Settings** (gear icon)
3. Navigate to **Connectors**
4. Click **Add custom connector**

### Step 2: Configure the Connector

- **Name:** `Google Meta Ads GA4`
- **MCP Server URL:** `YOUR_MCP_ENDPOINT_URL`
- **Authentication:** OAuth (will prompt on first use)

### Step 3: Save and Test

1. Click **Save**
2. Start a new chat
3. Type: `List all my Google Ads campaigns`
4. ChatGPT will request permission to use the connector — click **Allow**

---

## Usage Tips

### First-time setup for each platform

When you first use a platform's tools, you'll be prompted to authenticate:

- **Google Ads:** OAuth sign-in with your Google account
- **Meta Ads:** OAuth sign-in with your Facebook/Meta account
- **GA4:** Uses the same Google OAuth as Google Ads

### Platform prefixes

- Google Ads tools: no prefix (e.g., `list_campaigns`)
- Meta Ads tools: `meta_` prefix (e.g., `meta_get_campaigns`)
- GA4 tools: `ga_` prefix (e.g., `ga_run_report`)

### Best practices

1. Start each session by listing your accounts:
   - `"Show me my Google Ads accounts"`
   - `"List my Meta ad accounts"`
2. Be specific about date ranges: `"Show campaign performance for the last 7 days"`
3. Use natural language — ChatGPT will select the right tools automatically

---

## Troubleshooting

### Connector not appearing

- Ensure you have a ChatGPT Plus/Team/Enterprise subscription
- Check that Connectors is enabled in your account settings
- Try refreshing the page

### Authentication loop

- Clear your browser cookies for the OAuth provider
- Try in an incognito/private window
- Ensure third-party cookies are enabled during the OAuth flow

### Rate limiting

If you hit rate limits, wait a few minutes and try again. For bulk operations, space out your requests or use batch tools.
