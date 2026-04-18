# Naukri Job Scraper

Extract structured data from [Naukri.com](https://Naukri.com) — job listings from Naukri.com with keyword search, filters, and optional detail enrichment

**[Naukri.com Job Scraper - Incremental Mode Saves 83% on Daily Monitoring on Apify →](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi)**

---

## Key features





**Detail enrichment** — Fetch full job descriptions, structured metadata for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged, expired, cross-run repost detection across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings. Set to 0 for the full catalog.

**Proxy support** — Route traffic through Apify Proxy or your own proxy group to avoid regional blocks and rate limits.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Clean JSON output with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases





**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from Naukri.com on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from Naukri.com.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "maxResults": 50
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `keyword` | string | — | Job search keyword (e.g. 'python developer', 'data analyst'). Not required if jobIds is provided. |
| `jobIds` | array | — | Fetch specific jobs by their Naukri job IDs (skips keyword search). Each ID is fetched via the detail API. |
| `location` | string | — | Filter by location (e.g. 'Bangalore', 'Mumbai', 'Delhi') |
| `maxResults` | integer | `100` | Maximum number of jobs to return (0 = unlimited) |
| `fetchDetails` | boolean | `false` | Fetch full job descriptions and additional fields via detail API (slower but richer data) |
| `incremental` | boolean | `false` | Only return new or changed jobs since last run (state scoped per keyword+location) |
| `compact` | boolean | `false` | Return only core fields (jobId, title, company, location, salary, experience, skills, createdDate, portalUrl, description). Ideal for AI agents and MCP workflows. |
| `descriptionMaxLength` | integer | — | Truncate job descriptions to this many characters (0 or empty = no truncation) |
| `experienceMin` | integer | — | Minimum years of experience filter |
| `experienceMax` | integer | — | Maximum years of experience filter |
| `salary` | enum | — | Salary range filter in lakhs per annum |
| `sortBy` | enum | — | Sort results by relevance or posting date |
| `workMode` | enum | — | Filter by work arrangement |
| `freshness` | integer | — | Only show jobs posted within this many days (1, 3, 7, 15, or 30) |
| `maxConcurrency` | integer | `3` | Maximum number of concurrent requests |
| `maxRequestRetries` | integer | `3` | Maximum number of retries per request |
| `proxyConfiguration` | object | — | Apify proxy configuration (not required — the API works without proxy) |

---

## FAQ

**How to scrape naukri?**
Use this actor on Apify to extract structured job listings from Naukri.com. Set your search query and filters in the input, then run — no coding needed.

**Is there a naukri API?**
Naukri.com does not provide a public API. This actor works as an unofficial API, returning structured JSON data from naukri.

**Is it legal to scrape Naukri.com?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->


## Output fields

Every listing returns the same 35-field schema. Missing values are `null` — never omitted.

- `jobId`
- `title`
- `companyName`
- `companyId`
- `experienceText`
- `minimumExperience`
- `maximumExperience`
- `salary`
- `salaryMin`
- `salaryMax`
- `salaryCurrency`
- `location`
- `skills`
- `createdDate`
- `portalUrl`
- `logoPath`
- `industry`
- `viewCount`
- `companyWebsite`
- `ambitionBox`
- `description`
- `descriptionHtml`
- `descriptionMarkdown`
- `roleCategory`
- `functionalArea`
- `jobRole`
- `employmentType`
- `educationUG`
- `educationPG`
- `applyCount`
- `vacancy`
- `wfhType`
- `companyDescription`
- `scrapedAt`
- `searchKeyword`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "100426916818",
  "title": "Custom Software Engineer",
  "companyName": "Accenture",
  "companyId": 27117,
  "experienceText": "0-1 Yrs",
  "minimumExperience": 0,
  "maximumExperience": 1,
  "salary": "Not disclosed",
  "salaryMin": null,
  "salaryMax": null,
  "salaryCurrency": null,
  "location": "Chennai"
}
```

*Truncated — full records contain 35 fields. See Output fields for the complete schema.*


**[Try Naukri.com Job Scraper - Incremental Mode Saves 83% on Daily Monitoring now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data





- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Bilbasen Scraper](https://apify.com/blackfalcondata/bilbasen-scraper?fpr=1h3gvi) — Denmark's largest car marketplace


## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---
---

*Last updated: 2026 03*
