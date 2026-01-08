Job Discovery MCP
An enterprise-ready MCP (Model Context Protocol) server for discovering recent job listings across major job boards using JobSpy.
Built for LLM agents, MCP Inspectors, and AI platforms that need structured job-market data.
What it does
Searches multiple job boards in one call
Returns normalized, structured job listings
Enforces clear input contracts (no silent failures)
Docker-first and Cloud Run compatible
Supported Job Boards
Indeed
LinkedIn
Google Jobs
Glassdoor
ZipRecruiter
Bayt
Bdjobs
Naukri
Default: All boards
Tool: scrape_jobs_tool
Searches job boards and returns recent job listings based on role, location, and recency.
Parameters
Boards (List[string], optional)
Job boards to search. Defaults to all supported boards.
RoleKeywords (string, optional)
Job title or role keywords (e.g. “Product Manager”).
Location (string, optional)
City, region, or country (e.g. “Berlin”, “Remote”).
ResultCount (int, optional, default: 20)
Max number of jobs to return.
PostedWithinDays (int, optional, default: 7)
Only return jobs posted within this many days.
Country (string, conditionally required)
Required when using Indeed.
Must be a supported country name or alias (e.g. pakistan, united arab emirates, us).
Abbreviations like uae are not supported.
Output
Returns structured JSON with job details such as title, company, location, posting date, salary (if available), and URLs.
Run with Docker
docker build -t jobspy-mcp .
docker run -p 8080:8080 jobspy-mcp
MCP endpoint:
http://localhost:8080/mcp
Design principles
Human-friendly parameters
Strict validation, clear errors
LLM-discoverable descriptions
Stateless and production-safe
