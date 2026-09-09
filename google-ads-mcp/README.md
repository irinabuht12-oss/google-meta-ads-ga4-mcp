# Google Ads MCP Server

**Google Ads MCP** by [Ryze AI](https://www.get-ryze.ai): a hosted Model Context Protocol server that connects Claude, ChatGPT, Cursor, Claude Code, Grok, Windsurf and n8n to your Google Ads account. Audit campaigns, pull search terms, run GAQL, research keywords, and change budgets, bids and negatives with approval. No developer token, no Google Cloud project, no API key. Sign in with the Google account that owns the ads.

- Endpoint: `https://connector.get-ryze.ai/mcp` (Streamable HTTP, OAuth 2.1 with dynamic client registration and PKCE)
- Price: free to connect
- Setup guide with screenshots: https://www.get-ryze.ai/how-to-connect-claude-to-google-meta-ads-mcp
- Also in this connector: [Meta Ads MCP](../meta-ads-mcp/README.md), GA4, Google Search Console

## Install the Google Ads MCP

**Claude Code**

```
claude mcp add ryze --transport http https://connector.get-ryze.ai/mcp
```

**claude.ai and Claude Desktop**: Settings › Connectors › Add custom connector, name `Ryze`, URL `https://connector.get-ryze.ai/mcp`, then sign in with Google and choose Connect Google Ads.

**ChatGPT**: Settings › Connectors › Add custom connector (Developer mode), same URL.

**Cursor**: Settings › MCP › Add new MCP server, type `http`, same URL. Or `.cursor/mcp.json`:

```json
{ "mcpServers": { "google-ads": { "url": "https://connector.get-ryze.ai/mcp" } } }
```

**Grok**: grok.com/connectors › New Connector › Custom, same URL. Also available as a Grok Bot: https://x.ai/bot/dep-tU0gmIPgiqNsvS4N4

Manager (MCC) accounts are picked up automatically; every child account the signed-in user can access is available.

## What is a Google Ads MCP?

The Model Context Protocol (MCP) is the open standard that lets AI assistants call external tools. A Google Ads MCP server exposes the Google Ads API as MCP tools, so an assistant can read and change an ad account from a chat. This one is hosted and OAuth-based: Ryze holds the developer token and API access, you authorize with a normal Google login, nothing runs on your machine.

## Google Ads MCP tools

Tool names as the connector exposes them (namespace `google_ads__`):

| Tool | What it does |
|---|---|
| `google_ads__listAccessibleCustomers` | List every Google Ads account the login can access, including MCC children |
| `google_ads__getAccountHierarchy` | Manager account tree |
| `google_ads__getAccountSummary` | Spend, conversions, CPA, ROAS for a period |
| `google_ads__runRawGaql` | Any GAQL query: campaigns, ad groups, keywords, search terms, assets, change history |
| `google_ads__generateKeywordIdeas` | Keyword Planner ideas with volume, competition, CPC |
| `google_ads__generateKeywordHistoricalMetrics` | Monthly search volume history for a keyword list |
| `google_ads__listConversionActions` | Conversion actions and their status |
| `google_ads__listRecommendations` | Google's own recommendations for the account |
| `google_ads__applyRecommendation` / `dismissRecommendation` | Act on a recommendation (approval required) |
| `google_ads__runRawMutate` | Any write: pause, budgets, bids, negatives, RSA copy, labels (approval required) |
| `google_ads__runRawMutateDelete` | Remove entities (approval required) |
| `google_ads__runRawCustomAudienceMutate` | Create or edit custom audiences |
| `google_ads__uploadImageAsset` | Upload image assets for Performance Max and Display |

Reads run immediately. Writes are proposed in the chat and executed only after you confirm.

## Example prompts for the Google Ads MCP

- "Which search terms spent more than $50 with zero conversions in the last 30 days? Draft the negative keyword list."
- "Why did CPA rise this week? Break it down by campaign and ad group."
- "Show budget-capped campaigns and how much impression share we lose to budget."
- "Keyword ideas for 'running shoes' with volume, CPC and competition, grouped by intent."
- "Compare Performance Max vs Search ROAS for the last 90 days."
- "Pause every ad group with spend above $200 and no conversions this month." (asks for approval first)

## Google Ads MCP vs alternatives

| | Ryze Google Ads MCP | Official Google Ads MCP | Self-hosted open-source servers |
|---|---|---|---|
| Setup | 2 minutes, Google login | Developer token + Cloud project | 30 to 60 minutes, your own token |
| Access | Read and approved write | Read-only | Depends on server |
| Meta Ads, GA4, Search Console in the same connector | Yes | No | No |
| Runs on | Ryze hosted | Google hosted | Your machine or server |
| Cost | Free | Free | Free plus your API quota |

## FAQ

**Do I need a Google Ads developer token?** No. The connector is hosted; you sign in with Google and approve the standard permission screen.

**Is it read-only?** Reads are always on. Writes go through tools that wait for your approval inside the chat.

**Does it work with MCC manager accounts?** Yes, every child account under the manager appears automatically.

**Which clients work?** Anything that supports remote MCP over Streamable HTTP with OAuth: Claude, Claude Desktop, Claude Code, ChatGPT, Cursor, Grok, Windsurf, Cline, Gemini CLI, Codex CLI, n8n.

**Where do I get skills and prompts for it?** [48 free Claude marketing skills](https://github.com/irinabuht12-oss/marketing-skills) and [15 Claude skills for Google Ads](https://www.get-ryze.ai/blog/claude-skills-for-google-ads).

## Links

- Connector: https://connector.get-ryze.ai/mcp
- Setup guide: https://www.get-ryze.ai/how-to-connect-claude-to-google-meta-ads-mcp
- Google Ads and Claude, step by step: https://www.get-ryze.ai/blog/how-to-connect-google-ads-claude-mcp
- Official MCP registry entry: `io.github.irinabuht12-oss/google-meta-ads-ga4-mcp`
- Support: hello@get-ryze.ai
