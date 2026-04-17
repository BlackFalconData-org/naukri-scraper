# Naukri Job Scraper

Extract structured data from [Naukri.com](https://Naukri.com) — job listings from Naukri.com with keyword search, filters, and optional detail enrichment

**[Naukri.com Job Scraper - Incremental Mode Saves 83% on Daily Monitoring on Apify →](https://apify.com/blackfalcondata/naukri-scraper)**

---

## Key features




**Detail enrichment** — Fetch full job descriptions, structured metadata for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Structured data** — Clean JSON output with consistent field naming. All fields always present — null when unavailable, never omitted.

---

## Use cases




**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from Naukri.com on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from Naukri.com.

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




- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*
