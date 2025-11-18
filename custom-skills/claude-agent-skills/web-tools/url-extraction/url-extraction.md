---
name: url-extraction
description: URL and link extraction specialist. Use PROACTIVELY for finding, extracting, and cataloging all URLs and links within website codebases, including internal links, external links, API endpoints, and asset references.
enforcement_level: LOW
violation_consequence: URLs may be missed during extraction, leading to incomplete inventories and potential broken links
---

# URL Extraction

This skill provides comprehensive guidance for finding, extracting, and cataloging all URLs and links within website codebases.

## Overview

URL extraction involves scanning codebases to find and catalog all URLs and links across multiple file types and contexts. This skill provides systematic approaches to URL extraction as a URL and link extraction specialist.

## ✓ Pre-Extraction Checklist

**BEFORE extracting URLs, verify:**

```yaml
Checklist:
  - [ ] Codebase location identified
  - [ ] File types to scan determined
  - [ ] Extraction scope defined
  - [ ] Output format planned
  - [ ] Organization strategy determined
  - [ ] Validation approach planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective URL extraction
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-extraction verification complete: Ready to extract URLs"
- Proceed with: URL extraction workflow

## Link Types to Identify

- **Absolute URLs** (https://example.com)
- **Protocol-relative URLs** (//example.com)
- **Root-relative URLs** (/path/to/page)
- **Relative URLs** (../images/logo.png)
- **API endpoints** and fetch URLs
- **Asset references** (images, scripts, stylesheets)
- **Social media links**
- **Email links** (mailto:)
- **Tel links** (tel:)
- **Anchor links** (#section)
- **URLs in meta tags** and structured data

## Extraction Contexts

- HTML attributes (href, src, action, data attributes)
- JavaScript strings and template literals
- CSS url() functions
- Markdown link syntax [text](url)
- Configuration files (siteUrl, baseUrl, API endpoints)
- Environment variables referencing URLs
- Comments that contain URLs

## Organization Strategy

- Group URLs by type (internal vs external)
- Note file path and line number where each URL was found
- Identify duplicate URLs across files
- Flag potentially problematic URLs (hardcoded localhost, broken patterns)
- Categorize by purpose (navigation, assets, APIs, external resources)

## Output Deliverables

- Structured inventory in clear format (JSON or markdown table)
- Statistics (total URLs, unique URLs, external vs internal ratio)
- Highlight suspicious or potentially broken links
- Note inconsistent URL patterns
- Suggest areas that might need attention

## Best Practices

- Scan multiple file types comprehensively
- Handle edge cases and various URL formats
- Provide actionable output
- Include statistics and analysis
- Flag potential issues

## Tools and Methods

- **Read**: Analyze codebase files and structures
- **Write/Edit**: Create URL inventories and reports
- **Grep**: Search for URL patterns across files
- **Glob**: Find files by patterns
- **LS**: List directory structures

