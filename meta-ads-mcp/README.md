# Meta Ads MCP Server (Facebook and Instagram Ads)

**[Meta Ads MCP](https://www.get-ryze.ai/meta-ads-mcp)** by [Ryze AI](https://www.get-ryze.ai): a hosted Model Context Protocol server that connects Claude, ChatGPT, Cursor, Claude Code, Grok, Windsurf and n8n to your Meta ad accounts. Pull Insights for campaigns, ad sets and ads, spot creative fatigue, list creatives and lead forms, search the Meta Ad Library, and change budgets or pause ads with approval. No Meta app review, no access token to manage. Sign in with the Facebook user that has access in Business Manager.

- Endpoint: `https://connector.get-ryze.ai/mcp` (Streamable HTTP, OAuth 2.1 with dynamic client registration and PKCE)
- Price: free to connect
- Product page: https://www.get-ryze.ai/meta-ads-mcp
- Setup guide with screenshots: https://www.get-ryze.ai/how-to-connect-claude-to-google-meta-ads-mcp#meta-ads
- Also in this connector: [Google Ads MCP](../google-ads-mcp/README.md), GA4, Google Search Console

## Install the Meta Ads MCP

**Claude Code**

```
claude mcp add ryze --transport http https://connector.get-ryze.ai/mcp
```

**claude.ai and Claude Desktop**: Settings › Connectors › Add custom connector, name `Ryze`, URL `https://connector.get-ryze.ai/mcp`, then choose Connect Meta Ads and approve the Facebook permission screen (`ads_read`, `ads_management`).

**ChatGPT**: Settings › Connectors › Add custom connector (Developer mode), same URL.

**Cursor**: Settings › MCP › Add new MCP server, type `http`, same URL. Or `.cursor/mcp.json`:

```json
{ "mcpServers": { "meta-ads": { "url": "https://connector.get-ryze.ai/mcp" } } }
```

**Grok**: grok.com/connectors › New Connector › Custom, same URL. Also available as a Grok Bot: https://x.ai/bot/dep-tU0gmIPgiqNsvS4N4

Instagram placements come through the same ad account. You can limit access to specific ad accounts on the Facebook permission screen.

## What is a Meta Ads MCP?

The Model Context Protocol (MCP) is the open standard that lets AI assistants call external tools. A Meta Ads MCP server exposes the Meta Marketing API (Facebook Ads and Instagram Ads) as MCP tools, so an assistant can read performance and change the account from a chat. This one is hosted and OAuth-based: Ryze owns the Meta app and its permissions, you authorize with a normal Facebook login, nothing runs on your machine.

## Meta Ads MCP tools

Tool names as the connector exposes them (namespace `meta_ads__`):

| Tool | What it does |
|---|---|
| `meta_ads__listAdAccounts` | Every ad account the Facebook user can access |
| `meta_ads__getAccountSummary` | Spend, results, CPA, ROAS, frequency for a period |
| `meta_ads__runRawInsights` | Any Insights query: level, fields, breakdowns, date ranges, attribution windows |
| `meta_ads__listCreatives` / `getCreative` | Creatives with copy, media and destination |
| `meta_ads__listLeadForms` / `listLeads` | Lead forms and the leads they collected |
| `meta_ads__searchAdLibrary` | Competitor research in the Meta Ad Library by brand or keyword |
| `meta_ads__runGraphRead` | Any Graph API read: campaigns, ad sets, ads, audiences, pixels, pages |
| `meta_ads__runGraphWrite` | Any Graph API write: pause, budgets, bids, targeting, new ads (approval required) |
| `meta_ads__runGraphDelete` | Remove entities (approval required) |
| `meta_ads__uploadImageFromUrl` | Upload an image for a new creative |

Reads run immediately. Writes are proposed in the chat and executed only after you confirm.

## Example prompts for the Meta Ads MCP

- "Which ads have frequency above 3 and CTR down more than 20% from their peak this week?"
- "Break down last month's CPA by ad set and tell me which audiences overlap."
- "Pull spend, purchases and ROAS by campaign, 7-day click attribution, last 30 days."
- "Search the Ad Library for every active ad from [competitor] and group the hooks."
- "List leads from the spring form with the questions they answered."
- "Move $50 a day from the prospecting ad set to retargeting." (asks for approval first)

## Meta Ads MCP vs alternatives

| | Ryze Meta Ads MCP | Official Meta MCP | Self-hosted open-source servers |
|---|---|---|---|
| Setup | 2 minutes, Facebook login | Meta app + system user token | 30 to 60 minutes, your own token |
| Access | Read and approved write | Limited | Depends on server |
| Google Ads, GA4, Search Console in the same connector | Yes | No | No |
| Ad Library research | Yes | No | Rarely |
| Cost | Free | Free | Free plus your API quota |

## FAQ

**Do I need a Meta developer app or access token?** No. Ryze holds the app and permissions; you approve the standard Facebook permission screen.

**Does it cover Instagram ads?** Yes, Instagram placements run through the same Meta ad account.

**Is it read-only?** Reads are always on. Writes go through tools that wait for your approval inside the chat.

**Can I connect several Business Managers?** Yes, every ad account the signed-in user can access is available.

**Where do I get skills and prompts for it?** [48 free Claude marketing skills](https://github.com/irinabuht12-oss/marketing-skills) and [Claude skills for Meta Ads](https://www.get-ryze.ai/blog/claude-skills-for-meta-ads).

## Links

- Meta Ads MCP page: https://www.get-ryze.ai/meta-ads-mcp
- Connector: https://connector.get-ryze.ai/mcp
- Setup guide: https://www.get-ryze.ai/how-to-connect-claude-to-google-meta-ads-mcp
- Official MCP registry entry: `io.github.irinabuht12-oss/google-meta-ads-ga4-mcp`
- Support: hello@get-ryze.ai
