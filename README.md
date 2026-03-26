# Naukri Job Scraper

Extract structured data from [Naukri.com](https://Naukri.com) — job listings from Naukri.com with keyword search, filters, and optional detail enrichment

**[Run on Apify →](https://apify.com/blackfalcondata/naukri-scraper)**

---

## Key features

📄 **Detail enrichment**

Fetch full job descriptions, salary data, employer profiles, and contact information for each listing.

🔄 **Incremental mode**

Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

⚡ **Compact output for AI agents**

Core-fields-only mode optimized for MCP and AI agent workflows. Description truncation to control output size.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured job listings from naukri on a schedule. Export to CSV, JSON, or directly to your database.

**Market research**
Monitor job listings, track trends, and analyze market dynamics with structured, deduplicated data from naukri.

**AI and LLM workflows**
Use compact mode and description truncation to feed data into AI agents, MCP servers, and LLM pipelines without exceeding token budgets.

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

---

## Related products by Black Falcon Data

| Product | Description |
|:--------|:------------|
| [StepStone Jobs API](https://github.com/BlackFalconData-org/stepstone-jobs-api) | Job listings from 18 European portals |
| [Company Jobs Tracker](https://github.com/BlackFalconData-org/company-jobs-tracker-api) | Track new/removed jobs per company |
| [Indeed Jobs Feed](https://github.com/BlackFalconData-org/indeed-jobs-feed) | Indeed job listings with salary data |
| [Glassdoor Jobs Feed](https://github.com/BlackFalconData-org/glassdoor-jobs-feed) | Glassdoor listings with company ratings |
| [Arbeitsagentur Jobs Feed](https://github.com/BlackFalconData-org/arbeitsagentur-jobs-feed) | Germany's federal job portal (1M+ listings) |
| [Naukri Jobs Feed](https://github.com/BlackFalconData-org/naukri-jobs-feed) | India's largest job portal |
| [Bilbasen Scraper](https://github.com/BlackFalconData-org/bilbasen-scraper) | Denmark's largest car marketplace |

---

*Last updated: 2026 03*
