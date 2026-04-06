# Example Prompts & Use Cases

Real-world prompts you can use with any AI assistant connected to this MCP server.

---

## Google Ads

### Account Overview
```
Show me all my Google Ads accounts and their names
```

### Campaign Management
```
List all my active campaigns with their budgets and status
Create a new Search campaign called "Spring Sale 2026" with a $100/day budget
Pause all Display campaigns that have spent more than $500 with zero conversions
Resume my "Brand Search" campaign
Copy my best-performing campaign and rename it "Summer Variant"
```

### Performance Analysis
```
What are my top 10 campaigns by conversions this month?
Show me keyword performance for the "Brand Search" campaign, sorted by cost
Compare performance of my Search vs Shopping campaigns for the last 30 days
Which ad groups have the highest CPA? Show me the top 5
Calculate ROAS for each ad in my "Product Launch" campaign
```

### Keyword Research
```
Find keyword ideas for "best project management software" with search volumes
What's the average CPC for keywords related to "CRM software"?
Show me search terms that triggered my ads this week
Add "free" and "cheap" as negative keywords to all Search campaigns
Suggest negative keywords for my "Enterprise Software" campaign
```

### Bidding & Budgets
```
List all my shared budgets and which campaigns use them
Create a shared budget of $500/day for my brand campaigns
What's the bid adjustment performance by device for my top campaign?
Set mobile bid adjustment to +20% for my "Local Services" campaign
```

### Ad Creation
```
Create a responsive search ad for my "CRM Software" ad group with 15 headlines and 4 descriptions
What's the ad strength score for ads in my "Brand" campaign?
Show me ads with "Poor" or "Average" ad strength that I should improve
```

### Extensions
```
Create sitelink extensions for my brand campaign pointing to Pricing, Features, and Demo pages
Add callout extensions: "Free Trial", "24/7 Support", "No Credit Card Required"
List all my current extensions and which campaigns they're attached to
```

### Advanced
```
Run this GAQL query: SELECT campaign.name, metrics.cost_micros, metrics.conversions FROM campaign WHERE segments.date DURING LAST_30_DAYS
Create an A/B experiment splitting traffic 50/50 on my "Product" campaign
Set up conversion tracking for form submissions on my website
```

---

## Meta Ads

### Account Overview
```
List all my Meta ad accounts with their names and IDs
Show me business details for my Meta Business account
```

### Campaign Management
```
List all active Meta campaigns with their objectives and budgets
Create a new conversion campaign targeting US users aged 25-45
Update my "Summer Sale" campaign budget to $200/day
Delete the test campaign I created yesterday
```

### Performance Analysis
```
What's my Meta Ads spend and ROAS for the last 7 days?
Show me ad performance broken down by age and gender
Which ad sets have the lowest cost per lead?
Compare my Facebook vs Instagram placement performance
Get page insights for my business page this month
```

### Audience & Targeting
```
Create a custom audience from my customer email list
Build a 1% lookalike audience based on my purchasers
What's the estimated audience size for women aged 25-34 interested in fitness in the US?
Search for interest targets related to "digital marketing"
Find behavior targets for "small business owners"
```

### Creative Management
```
Upload this image and create a new ad creative for my awareness campaign
Show me previews of my latest ad creatives
Which ad creatives have the highest CTR?
Create a new carousel ad with 3 product images
```

### Lead Generation
```
List all lead forms in my account
Show me the latest 50 leads from my "Free Consultation" form
Create a test lead for my lead form to verify the integration
```

### Product Catalogs
```
List all products in my catalog
Add a new product to my catalog with price $49.99
Update prices for all products in the "Summer Collection" set
Create a new product feed from my website URL
```

---

## Google Analytics 4

### Reporting
```
Show me a realtime report of users on my site right now
How many sessions did I get from organic search this month?
Run a report showing top 10 pages by pageviews for the last 30 days
What's my bounce rate by traffic source?
Compare this month's conversions to last month
```

### Configuration
```
List all data streams for my GA4 property
What custom dimensions and metrics do I have configured?
Show me my data retention settings
What enhanced measurement events are enabled?
Check my attribution settings — am I using data-driven or last-click?
```

### Audiences & Events
```
List all configured audiences in my GA4 property
What are my key events (conversions)?
Show me all channel groups and their definitions
```

### Integrations
```
Do I have BigQuery linked to my GA4 property?
List all Firebase links for my property
Check if Search Ads 360 is connected to my GA4
```

---

## Cross-Platform Analysis

### Spend Comparison
```
Compare my total Google Ads and Meta Ads spend for March 2026
Which platform gives me better ROAS — Google or Meta?
Show me daily spend trends across both platforms for the last 30 days
```

### Conversion Analysis
```
Pull GA4 conversion data and compare it with Google Ads reported conversions
Which platform is driving more form submissions — Google Ads or Meta Ads?
Show me the customer journey: which channels assist conversions in GA4?
```

### Budget Optimization
```
I have $10,000/month to split between Google and Meta. Based on last month's performance, what's the optimal allocation?
Which campaigns across both platforms should I increase budget on based on ROAS?
```

### Reporting
```
Create a comprehensive weekly report covering:
1. Google Ads: top campaigns, spend, conversions, ROAS
2. Meta Ads: top campaigns, spend, leads, CPA
3. GA4: total sessions, conversion rate, top channels
```

---

## n8n Automation Examples

### Scheduled Reports
```
Every Monday at 9am, pull last week's Google Ads and Meta Ads performance,
format as a summary, and send to Slack channel #marketing-reports
```

### Alert Workflows
```
Every hour, check if any Google Ads campaign has overspent its daily budget by 20%.
If so, pause it and send an alert to the marketing team
```

### Data Sync
```
Daily at midnight, pull all Meta Ads lead form submissions from today
and add them to our Google Sheet CRM tracker
```
