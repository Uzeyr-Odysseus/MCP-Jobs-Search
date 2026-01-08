## Job Discovery MCP

**Job Discovery MCP** is an enterprise-ready **Model Context Protocol (MCP) server** that aggregates job listings from popular job boards into a single, LLM-friendly tool.

It wraps **JobSpy** behind a clean MCP interface, making job discovery usable by AI agents, MCP Inspectors, and production systems.

---

## Features

- Searches job postings across **LinkedIn**, **Indeed**, **Glassdoor**, **Google Jobs**, **ZipRecruiter**, **Bayt**, **Bdjobs**, and **Naukri**
- Single MCP tool with human-friendly parameters
- Normalized, structured job listings
- Strict validation with clear, actionable errors
- Docker-first and Cloud Run compatible

---

## Tool

### `scrape_jobs_tool`

Searches multiple job boards and returns recent job listings based on role, location, and posting recency.

---

## Parameters

- **Boards** *(List[string], optional)*  
  Job boards to search.  
  Defaults to all supported boards.

- **RoleKeywords** *(string, optional)*  
  Role or job title keywords (e.g. `"Product Manager"`).

- **Location** *(string, optional)*  
  City, region, country, or `"Remote"`.

- **ResultCount** *(integer, optional — default: 20)*  
  Maximum number of jobs to return.

- **PostedWithinDays** *(integer, optional — default: 7)*  
  Only return jobs posted within this many days.

- **Country** *(string, conditionally required)*  
  Required **only when using Indeed**.  
  Must be a supported country name or alias (e.g. `pakistan`, `united arab emirates`, `us`).  
  Abbreviations like `uae` are **not supported**.

---

## Output

Returns structured JSON containing job metadata such as title, company, location, posting date, salary (if available), and URLs.

---

## Run with Docker

```bash
docker build -t jobspy-mcp .
docker run -p 3333:3333 jobspy-mcp
