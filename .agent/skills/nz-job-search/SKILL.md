---
name: nz-job-search
description: Finds current New Zealand software engineering leadership jobs matching specific criteria. Use when searching for NZ tech jobs, leadership roles in Christchurch or remote NZ positions, or when the user asks to "find NZ jobs", "search for tech lead roles in NZ", "find Christchurch software jobs", "search for NZ engineering manager positions", or similar job search requests focused on New Zealand.
---

# NZ Job Search

Find current New Zealand software engineering leadership jobs with precise filtering and structured output.

## Overview

This skill helps search for NZ-based software engineering leadership positions with strict criteria:
- **Leadership roles only** (Tech Lead, Engineering Team Lead, Engineering Manager)
- **Location**: Christchurch or Remote within NZ only
- **Recency**: Posted within last 7 days if not specified otherwise
- **Structured output**: Markdown table with verification

## Role Criteria

Include jobs with these titles:
- Tech Lead / Technical Lead
- Lead Developer / Lead Software Engineer
- Engineering Team Lead
- Hands-on Software Engineering Manager

**Requirements**:
- Must involve technical leadership AND team responsibility
- Not just senior individual contributor work

## Location Criteria

Jobs must be:
- Located in **Christchurch, New Zealand**, OR
- **Remote within New Zealand only** (not "global remote")

## Time Filter (Critical)

**Only include roles posted within the last 7 days if not specified otherwise**

If you cannot verify the posting date → **exclude the job**.

## Exclusions

Do NOT include:
- ❌ Senior engineers with no leadership scope
- ❌ Pure architect/principal roles without team leadership
- ❌ Recruiter talent pools
- ❌ Roles outside NZ

## Search Workflow

### Step 1: Execute Web Search

Use web search with queries like:
- "Tech Lead Christchurch New Zealand"
- "Engineering Manager remote New Zealand"
- "Software Engineering Team Lead NZ"
- "Lead Developer Christchurch"

Search multiple job boards:
- Seek.co.nz
- TradeMe Jobs
- LinkedIn Jobs (NZ)
- Indeed NZ
- Company career pages

### Step 2: Filter Results

For each job found, verify:
1. ✅ **NZ-based or NZ-remote** (not global remote)
2. ✅ **Leadership responsibilities clearly stated** (not just senior IC)
3. ✅ **Posted within 7 days** (check posting date)
4. ✅ **Link is valid** (goes to exact job listing, not search page)

If any check fails → exclude the job.

### Step 3: Extract Information

For each valid job, extract:
- Job Title
- Company
- Location / Remote status
- Posted Date
- Leadership Scope (1 line summary)
- Tech Stack (if listed)
- Job Link (exact URL to listing)

### Step 4: Format Output

Return results in this **exact format**:

## Output Format (STRICT)

Return a markdown table:

| Job Title | Company | Location / Remote | Posted Date | Leadership Scope (1 line) | Tech Stack (if listed) | Job Link |
|-----------|---------|-------------------|-------------|---------------------------|------------------------|----------|
| [Title] | [Company] | [Location] | [Date] | [Leadership summary] | [Stack] | [URL] |

**Rules**:
- "Location / Remote" must be written exactly like:
  - `Christchurch (Onsite/Hybrid)` OR
  - `Remote – NZ Only`
- Links must go to the **exact job listing**, not search pages
- Do not include more than 10 roles
- **Do not invent or guess missing information**

### Step 5: Add Market Observations

After the table, add:

**Market Observations** (max 5 bullets):
- Short insights about hiring trends
- Tech stacks being requested
- Remote vs onsite patterns
- Salary ranges if visible
- Any notable patterns

## Handling Low Results

If fewer than 3 roles match all criteria, return what is available and state:

> "Limited fresh listings found this week."

This is normal - leadership roles with strict criteria may have limited availability.

## Example Output

```markdown
| Job Title | Company | Location / Remote | Posted Date | Leadership Scope (1 line) | Tech Stack (if listed) | Job Link |
|-----------|---------|-------------------|-------------|---------------------------|------------------------|----------|
| Engineering Team Lead | Acme Corp | Christchurch (Hybrid) | 2 days ago | Lead team of 5 engineers, own delivery and architecture | React, Node.js, AWS | https://... |
| Tech Lead | StartupXYZ | Remote – NZ Only | 5 days ago | Technical leadership for 4-person squad, mentor developers | Python, Django, GCP | https://... |

**Market Observations**:
- Most roles require cloud experience (AWS/Azure/GCP)
- Hybrid work is standard for Christchurch positions
- React/TypeScript dominates frontend requirements
- Salary ranges: $120k-$160k NZD for Tech Lead level
- Limited pure remote roles, most are Christchurch-based hybrid
```

## Verification Checklist

Before returning results, silently confirm for each job:
- [ ] NZ-based or NZ-remote (not global)
- [ ] Leadership responsibilities clearly stated
- [ ] Posted within 7 days
- [ ] Link is valid and goes to exact listing
- [ ] All required information extracted
- [ ] No invented or guessed data

## Tips for Effective Searches

1. **Use multiple search queries** - Different job boards use different terminology
2. **Check company career pages** - Not all jobs are on aggregators
3. **Verify posting dates carefully** - Some boards show "refreshed" dates, not original posting
4. **Read job descriptions fully** - Ensure leadership scope is explicit
5. **Be strict with criteria** - Better to return fewer high-quality matches than include questionable ones
