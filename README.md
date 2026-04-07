# Google Ads + Meta Ads + GA4 — MCP Server

> **The unified MCP server for managing Google Ads, Meta (Facebook/Instagram) Ads, and Google Analytics 4 from any AI assistant.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![MCP Protocol](https://img.shields.io/badge/MCP-Protocol-blue)](https://modelcontextprotocol.io)
[![Google Ads](https://img.shields.io/badge/Google%20Ads-API%20v20-4285F4?logo=google-ads&logoColor=white)](#google-ads-tools)
[![Meta Ads](https://img.shields.io/badge/Meta%20Ads-Marketing%20API-0081FB?logo=meta&logoColor=white)](#meta-ads-tools)
[![GA4](https://img.shields.io/badge/GA4-Data%20API-E37400?logo=google-analytics&logoColor=white)](#google-analytics-4-tools)
[![Powered by Ryze AI](https://img.shields.io/badge/Powered%20by-Ryze%20AI-FF6B35?logo=rocket&logoColor=white)](https://www.get-ryze.ai/)

<!-- ![Banner](assets/banner.png) -->

### Watch: Google Ads & Meta Ads Account Audit with Claude MCP

> See how to run a full Google Ads and Meta Ads account audit using Claude with MCP — from data pull to automated audit report and presentation, in minutes instead of hours.

https://github.com/user-attachments/assets/2f931292-a3af-4010-a72e-38b8cf6e62ba

**What you'll see:** Connect your ad accounts → Claude analyzes campaign performance, budget efficiency, and targeting gaps across Google Ads & Meta Ads → generates a complete audit report with recommendations → builds a ready-to-share presentation. **[Try it free on Ryze AI →](https://www.get-ryze.ai/)**

One MCP server. Three platforms. **250+ tools.** Manage all your advertising and analytics from ChatGPT, Claude, Cursor, n8n, Windsurf, and more. Powered by [Ryze AI](https://www.get-ryze.ai/).

---

## Why This Exists

Marketers and agencies juggle Google Ads, Meta Ads, and GA4 daily — each with its own dashboard, API, and workflow. Existing MCP servers only cover **one platform at a time**, forcing you to install and configure multiple tools.

**This server unifies everything:**

| Problem | Solution |
|---------|----------|
| Separate MCP servers per platform | One server, all platforms |
| Complex local setup with API keys | Remote MCP — connect in 2 minutes |
| Read-only access (official Google MCP) | Full read + write across all platforms |
| No analytics integration | GA4 built-in for data-driven decisions |

---

## Works With

| AI Assistant | Status | Setup Guide |
|:------------|:------:|:-----------:|
| ChatGPT | **Supported** | [Setup Guide](docs/SETUP_CHATGPT.md) |
| Claude Desktop | **Supported** | [Setup Guide](docs/SETUP_CLAUDE.md) |
| Claude Code | **Supported** | [Setup Guide](docs/SETUP_CLAUDE.md#claude-code) |
| Cursor | **Supported** | [Setup Guide](docs/SETUP_CURSOR.md) |
| Windsurf | **Supported** | [Setup Guide](docs/SETUP_WINDSURF.md) |
| n8n | **Supported** | [Setup Guide](docs/SETUP_N8N.md) |
| Codex CLI | **Supported** | [Config](configs/codex_config.toml) |
| Gemini CLI | **Supported** | [Setup Guide](docs/SETUP_CLAUDE.md#gemini-cli) |
| Cline | **Supported** | [Setup Guide](docs/SETUP_CURSOR.md#cline) |

---

## Features

### Google Ads (150+ tools)

- **Campaign Management** — Create, update, pause, and delete Search, Display, Shopping, PMax, Demand Gen, Video, and App campaigns
- **Keyword Research** — Keyword Planner integration with volume, CPC, and competition data
- **Bidding & Budgets** — Portfolio strategies, shared budgets, bid adjustments by device/location/schedule
- **Ad Creation** — Responsive Search Ads, Display Ads, Demand Gen Ads, App Ads with full creative control
- **Audience Targeting** — Custom audiences, remarketing lists, customer match, combined audiences
- **Performance Analytics** — Campaign/ad group/keyword/ad-level metrics, search terms, ROAS calculations
- **Extensions** — Sitelinks, callouts, calls, images, prices, promotions, structured snippets, lead forms
- **Experiments** — A/B testing with experiment creation, scheduling, and promotion
- **Negative Keywords** — Campaign-level, shared sets, auto-suggestions
- **Labels & Organization** — Create and apply labels across campaigns, ad groups, and ads
- **Conversion Tracking** — Create actions, upload conversions, custom variables, value rules

### Meta Ads (80+ tools)

- **Campaign CRUD** — Create, read, update, and delete campaigns with full objective support
- **Ad Set Management** — Budget, schedule, placement, and optimization controls
- **Creative Management** — Ad creatives, image/video upload, carousel and collection formats
- **Audience Targeting** — Custom audiences, lookalikes, interest/behavior/demographic targeting
- **Lead Generation** — Lead forms, lead retrieval, test leads
- **Product Catalogs** — Catalog management, product feeds, product sets
- **Performance Insights** — Account/campaign/ad set/ad-level metrics with breakdowns
- **Page Management** — Page posts, promotable posts, page insights, boosted posts
- **Business Management** — Business info, users, pages, Instagram accounts, pixels

### Google Analytics 4 (20+ tools)

- **Reporting** — Run standard reports, pivot reports, and realtime reports
- **Audience Analysis** — List audiences, channel groups, and segments
- **Property Configuration** — Data streams, enhanced measurement, data retention settings
- **Attribution** — Attribution settings and model configuration
- **Key Events** — List and analyze conversion events
- **Integrations** — BigQuery links, DV360 links, Search Ads links, Firebase links
- **Annotations** — Property-level annotations for tracking changes
- **Metadata** — Available dimensions, metrics, and compatibility checks

### Cross-Platform Capabilities

- Compare Google Ads vs Meta Ads campaign performance side by side
- Correlate ad spend with GA4 conversion data
- Unified ROAS analysis across platforms
- Cross-platform budget allocation recommendations

---

## Quick Start

### Claude Desktop (Recommended)

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "google-meta-ads-ga4": {
      "url": "YOUR_MCP_ENDPOINT_URL"
    }
  }
}
```

> **Config file location:**
> - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
> - Windows: `%APPDATA%\Claude\claude_desktop_config.json`

See the full [Claude Setup Guide](docs/SETUP_CLAUDE.md) for detailed instructions.

### ChatGPT

1. Go to **Settings** > **Connectors** > **Add custom connector**
2. Enter the MCP endpoint URL: `YOUR_MCP_ENDPOINT_URL`
3. Name it `Google Meta Ads GA4`
4. Click **Save**

See the full [ChatGPT Setup Guide](docs/SETUP_CHATGPT.md).

### Cursor / Windsurf

Add to your MCP config (`~/.cursor/mcp.json` or `~/.codeium/windsurf/mcp_config.json`):

```json
{
  "mcpServers": {
    "google-meta-ads-ga4": {
      "url": "YOUR_MCP_ENDPOINT_URL"
    }
  }
}
```

### n8n

Use the **MCP Server Trigger** node with Streamable HTTP:

1. Add an **MCP Client** node to your workflow
2. Set the Server URL to: `YOUR_MCP_ENDPOINT_URL`
3. Enable Bearer authentication (recommended)

See the full [n8n Setup Guide](docs/SETUP_N8N.md) or import the [ready-made workflow template](configs/n8n_workflow.json).

### Claude Code

```bash
claude mcp add google-meta-ads-ga4 --transport sse YOUR_MCP_ENDPOINT_URL
```

---

## Example Prompts

### Google Ads

```
"Show me all my Google Ads campaigns and their performance this month"
"Create a new Search campaign targeting 'best CRM software' keywords with a $50/day budget"
"What are my top 10 keywords by conversions in the last 30 days?"
"Pause all campaigns with ROAS below 2.0"
"Add negative keywords 'free' and 'cheap' to all my Search campaigns"
"Generate keyword ideas for 'project management tools' with volume data"
```

### Meta Ads

```
"List all active Meta ad campaigns and their spend this week"
"Create a lookalike audience based on my top purchasers"
"What's the CPL for my lead generation campaigns on Facebook?"
"Upload this image and create a new ad creative for my awareness campaign"
"Show me ad performance broken down by age and gender"
"Boost my latest page post with a $100 budget targeting US users"
```

### Google Analytics 4

```
"Show me a realtime report of active users on my website right now"
"What are my top traffic sources by conversions this month?"
"List all key events configured in my GA4 property"
"Run a report comparing organic vs paid traffic for the last 90 days"
"What custom dimensions and metrics do I have set up?"
```

### Cross-Platform

```
"Compare my Google Ads and Meta Ads ROAS for Q1 2026"
"Which platform is driving more conversions per dollar spent?"
"Show me all campaigns across Google and Meta with spend over $1000 this month"
"Correlate my GA4 conversion events with Google Ads campaign performance"
```

---

## Architecture

```
+------------------+     +------------------------+     +------------------+
|                  |     |                        |     |                  |
|  ChatGPT         |     |                        |     |  Google Ads API  |
|  Claude          |     |   MCP Server           |     |                  |
|  Cursor          +---->+   (Remote/Hosted)       +---->+  Meta Ads API    |
|  n8n             |     |                        |     |                  |
|  Windsurf        |     |   250+ Tools           |     |  GA4 Data API    |
|  Codex           |     |   OAuth 2.1 + PKCE     |     |                  |
|                  |     |                        |     |                  |
+------------------+     +------------------------+     +------------------+
    AI Assistants           Model Context Protocol         Ad & Analytics
                                                            Platforms
```

Your AI assistant communicates with this MCP server using the [Model Context Protocol](https://modelcontextprotocol.io). The server handles authentication and routes requests to the appropriate Google Ads, Meta Ads, or GA4 API.

---

## All Available Tools

<details>
<summary><strong>Google Ads Tools (150+)</strong> — Click to expand</summary>

#### Account & Campaign Management
| Tool | Description |
|------|-------------|
| `list_accounts` | List all accessible Google Ads accounts |
| `get_account_info` | Get detailed account information |
| `get_account_hierarchy` | View account hierarchy (MCC structure) |
| `list_campaigns` | List all campaigns with status and metrics |
| `get_campaign` | Get detailed campaign information |
| `create_search_campaign` | Create a new Search campaign |
| `create_display_campaign` | Create a new Display campaign |
| `create_shopping_campaign` | Create a new Shopping campaign |
| `create_pmax_campaign` | Create a Performance Max campaign |
| `create_demand_gen_campaign` | Create a Demand Gen campaign |
| `create_app_campaign` | Create an App campaign |
| `copy_campaign` | Duplicate an existing campaign |
| `update_campaign` | Update campaign settings |
| `pause_campaign` | Pause a campaign |
| `resume_campaign` | Resume a paused campaign |
| `delete_campaign` | Delete a campaign |

#### Ad Groups & Ads
| Tool | Description |
|------|-------------|
| `list_ad_groups` | List ad groups in a campaign |
| `create_ad_group` | Create a new ad group |
| `update_ad_group` | Update ad group settings |
| `pause_ad_group` | Pause an ad group |
| `enable_ad_group` | Enable an ad group |
| `delete_ad_group` | Delete an ad group |
| `list_ads` | List ads in an ad group |
| `get_ad` | Get ad details |
| `create_responsive_search_ad` | Create a Responsive Search Ad |
| `create_responsive_display_ad` | Create a Responsive Display Ad |
| `create_demand_gen_ad` | Create a Demand Gen ad |
| `update_ad` | Update an ad |
| `pause_ad` | Pause an ad |
| `enable_ad` | Enable an ad |
| `delete_ad` | Delete an ad |

#### Keywords & Targeting
| Tool | Description |
|------|-------------|
| `list_keywords` | List keywords in an ad group |
| `add_keywords` | Add keywords to an ad group |
| `update_keyword_bid` | Update keyword bids |
| `pause_keyword` | Pause a keyword |
| `enable_keyword` | Enable a keyword |
| `delete_keyword` | Delete a keyword |
| `keyword_planner` | Get keyword ideas with volume data |
| `add_negative_keywords` | Add negative keywords |
| `add_campaign_negative_keyword` | Add campaign-level negatives |
| `auto_suggest_negative_keywords` | AI-suggested negative keywords |
| `get_search_terms_insights` | Search terms report |
| `add_audience_targeting` | Add audience targeting |
| `set_demographic_targeting` | Set demographic targets |
| `add_campaign_location_targeting` | Add location targeting |
| `search_geo_locations` | Search for geo targets |

#### Bidding & Budgets
| Tool | Description |
|------|-------------|
| `list_budgets` | List all budgets |
| `create_budget` | Create a new budget |
| `update_budget` | Update budget amount |
| `list_bidding_strategies` | List bidding strategies |
| `create_portfolio_bidding_strategy` | Create portfolio strategy |
| `set_bid_adjustments` | Set bid adjustments |
| `get_bid_adjustment_performance` | Bid adjustment performance |

#### Extensions
| Tool | Description |
|------|-------------|
| `create_sitelink_extensions` | Create sitelink extensions |
| `create_callout_extensions` | Create callout extensions |
| `create_call_extensions` | Create call extensions |
| `create_image_extensions` | Create image extensions |
| `create_price_extensions` | Create price extensions |
| `create_promotion_extensions` | Create promotion extensions |
| `create_structured_snippet_extensions` | Create structured snippets |
| `create_lead_form_extensions` | Create lead form extensions |
| `list_extensions` | List all extensions |

#### Performance & Analytics
| Tool | Description |
|------|-------------|
| `get_campaign_overview` | Campaign performance overview |
| `get_keyword_performance` | Keyword performance metrics |
| `get_device_performance` | Performance by device |
| `get_location_performance` | Performance by location |
| `get_audience_performance` | Audience performance |
| `get_ad_strength_and_review_status` | Ad strength scores |
| `calculate_roas_by_ad` | ROAS calculation per ad |
| `compare_ad_performance` | Compare ad variants |
| `identify_optimization_opportunities` | AI optimization suggestions |
| `run_gaql_query` | Run custom GAQL queries |

#### Advanced Features
| Tool | Description |
|------|-------------|
| `create_experiment` | Create A/B test experiment |
| `schedule_experiment` | Schedule experiment run |
| `promote_experiment` | Promote winning variant |
| `create_conversion_action` | Create conversion action |
| `upload_click_conversions` | Upload offline conversions |
| `create_shared_set` | Create shared keyword set |
| `create_label` | Create organizational label |
| `create_custom_audience` | Create custom audience |
| `create_remarketing_action` | Create remarketing tag |

</details>

<details>
<summary><strong>Meta Ads Tools (80+)</strong> — Click to expand</summary>

#### Account & Campaign Management
| Tool | Description |
|------|-------------|
| `meta_get_ad_accounts` | List all Meta ad accounts |
| `meta_get_account_info` | Get ad account details |
| `meta_get_campaigns` | List all campaigns |
| `meta_get_campaign_details` | Get campaign details |
| `meta_create_campaign` | Create a new campaign |
| `meta_update_campaign` | Update campaign settings |
| `meta_delete_campaign` | Delete a campaign |

#### Ad Sets & Ads
| Tool | Description |
|------|-------------|
| `meta_get_adsets` | List ad sets |
| `meta_get_adset_details` | Get ad set details |
| `meta_create_adset` | Create an ad set |
| `meta_update_adset` | Update ad set |
| `meta_delete_adset` | Delete an ad set |
| `meta_get_ads` | List ads |
| `meta_get_ad_details` | Get ad details |
| `meta_create_ad` | Create an ad |
| `meta_update_ad` | Update an ad |
| `meta_delete_ad` | Delete an ad |

#### Creatives & Assets
| Tool | Description |
|------|-------------|
| `meta_get_ad_creatives` | List ad creatives |
| `meta_create_ad_creative` | Create ad creative |
| `meta_update_ad_creative` | Update ad creative |
| `meta_delete_ad_creative` | Delete ad creative |
| `meta_upload_ad_image` | Upload ad image |
| `meta_upload_ad_video` | Upload ad video |
| `meta_batch_upload_ad_images` | Batch upload images |
| `meta_get_ad_image` | Get image details |
| `meta_get_ad_previews` | Preview ad creatives |

#### Audiences & Targeting
| Tool | Description |
|------|-------------|
| `meta_create_custom_audience` | Create custom audience |
| `meta_create_lookalike_audience` | Create lookalike audience |
| `meta_estimate_audience_size` | Estimate audience reach |
| `meta_search_interests` | Search interest targets |
| `meta_search_behaviors` | Search behavior targets |
| `meta_search_demographics` | Search demographic targets |
| `meta_search_geo_locations` | Search geo locations |
| `meta_get_interest_suggestions` | Interest suggestions |

#### Performance & Insights
| Tool | Description |
|------|-------------|
| `meta_get_insights` | Get performance insights |
| `meta_get_page_insights` | Page-level insights |
| `meta_get_page_posts` | List page posts |
| `meta_get_promotable_posts` | Get promotable posts |
| `meta_boost_page_post` | Boost a page post |

#### Lead Generation
| Tool | Description |
|------|-------------|
| `meta_get_lead_forms` | List lead forms |
| `meta_get_lead_form_details` | Lead form details |
| `meta_get_lead_form_leads` | Get form submissions |
| `meta_create_lead_form` | Create lead form |
| `meta_create_test_lead` | Create test lead |

#### Product Catalogs
| Tool | Description |
|------|-------------|
| `meta_get_catalogs` | List catalogs |
| `meta_get_catalog_products` | List products |
| `meta_create_catalog_product` | Create product |
| `meta_batch_update_catalog_products` | Batch update products |
| `meta_create_catalog_product_feed` | Create product feed |
| `meta_create_catalog_product_set` | Create product set |

#### Business Management
| Tool | Description |
|------|-------------|
| `meta_get_business_info` | Get business details |
| `meta_get_business_users` | List business users |
| `meta_get_business_pages` | List business pages |
| `meta_get_business_ad_accounts` | Business ad accounts |
| `meta_get_business_instagram_accounts` | Instagram accounts |
| `meta_get_business_pixels` | List pixels |

</details>

<details>
<summary><strong>Google Analytics 4 Tools (20+)</strong> — Click to expand</summary>

| Tool | Description |
|------|-------------|
| `ga_get_account_summaries` | List all GA4 accounts and properties |
| `ga_get_property_details` | Get property configuration |
| `ga_run_report` | Run a standard report |
| `ga_run_pivot_report` | Run a pivot table report |
| `ga_run_realtime_report` | Run a realtime report |
| `ga_batch_run_reports` | Run multiple reports at once |
| `ga_get_metadata` | Get available dimensions and metrics |
| `ga_check_compatibility` | Check dimension/metric compatibility |
| `ga_list_audiences` | List configured audiences |
| `ga_list_key_events` | List key events (conversions) |
| `ga_list_data_streams` | List data streams |
| `ga_list_channel_groups` | List channel groups |
| `ga_get_custom_dimensions_and_metrics` | Custom dimensions/metrics |
| `ga_get_attribution_settings` | Attribution model settings |
| `ga_get_enhanced_measurement_settings` | Enhanced measurement config |
| `ga_get_data_retention_settings` | Data retention settings |
| `ga_get_google_signals_settings` | Google Signals status |
| `ga_list_bigquery_links` | BigQuery export links |
| `ga_list_dv360_links` | DV360 integration links |
| `ga_list_firebase_links` | Firebase integration links |
| `ga_list_search_ads_links` | Search Ads 360 links |
| `ga_list_property_annotations` | Property annotations |

</details>

<details>
<summary><strong>Research Tools</strong> — Click to expand</summary>

| Tool | Description |
|------|-------------|
| `research_google_search` | Search Google for market research |
| `research_analyze_webpage` | Analyze any webpage |
| `research_fetch_images_from_url` | Extract images from URLs |
| `research_download_and_resize` | Download and resize images |
| `research_search_stock_images` | Search stock image libraries |
| `research_get_landing_pages` | Analyze landing pages |

</details>

---

## Security & Privacy

- **OAuth 2.1 with PKCE** — Industry-standard authentication
- **No data storage** — The server does not store your ad data or credentials
- **Your tokens stay local** — Authentication tokens are stored on your machine only
- **Read-only by default** — Write operations require explicit confirmation
- **Scoped access** — Request only the permissions you need

---

## FAQ

<details>
<summary><strong>Do I need API keys for each platform?</strong></summary>

No. The MCP server handles authentication via OAuth. You'll be prompted to connect your Google and Meta accounts on first use.
</details>

<details>
<summary><strong>Is this free to use?</strong></summary>

Yes, the MCP server is free. You only pay for the AI assistant you use (ChatGPT, Claude, etc.) and any ad spend on the platforms.
</details>

<details>
<summary><strong>Can I use this with n8n for automation?</strong></summary>

Yes! See the [n8n Setup Guide](docs/SETUP_N8N.md) for Streamable HTTP integration, or import our [ready-made workflow template](configs/n8n_workflow.json).
</details>

<details>
<summary><strong>Does this support Google Ads Manager (MCC) accounts?</strong></summary>

Yes. The `get_account_hierarchy` and `list_accounts` tools support MCC structures, letting you manage multiple accounts from one connection.
</details>

<details>
<summary><strong>Can I run custom queries?</strong></summary>

Yes. Use `run_gaql_query` for Google Ads (GAQL) and `meta_fetch` for Meta Ads to run custom API queries.
</details>

<details>
<summary><strong>What about rate limits?</strong></summary>

The server respects Google and Meta API rate limits automatically. For high-volume operations, use batch tools like `add_batch_campaign_operations` and `meta_batch_update_catalog_products`.
</details>

---

## Contributing

Contributions are welcome! Please see our [issue templates](.github/ISSUE_TEMPLATE/) to report bugs or request features.

1. Fork this repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## Star History

If this project helps you manage ads more efficiently, please give it a star! It helps others discover it.

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <strong>Google Ads MCP</strong> · <strong>Meta Ads MCP</strong> · <strong>Facebook Ads MCP</strong> · <strong>GA4 MCP</strong> · <strong>Model Context Protocol</strong>
  <br>
  Built for marketers, agencies, and developers who want AI-powered ad management.
  <br><br>
  <a href="https://www.get-ryze.ai/">🚀 Get started with Ryze AI</a>
</p>
