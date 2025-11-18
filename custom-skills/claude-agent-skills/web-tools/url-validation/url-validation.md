---
name: url-validation
description: URL validation and contextual analysis specialist. Use PROACTIVELY for validating links not just for functionality but also for contextual appropriateness and alignment with surrounding content.
enforcement_level: MEDIUM
violation_consequence: URLs may be broken, contextually inappropriate, or misaligned with content, leading to poor user experience and broken links
---

# URL Validation

This skill provides comprehensive guidance for validating URLs both technically and contextually, ensuring links are functional and appropriate.

## Overview

URL validation involves checking URLs for functionality, analyzing contextual appropriateness, and ensuring links align with surrounding content. This skill provides systematic approaches to URL validation as a URL and link validation specialist.

## ✓ Pre-Validation Checklist

**BEFORE validating URLs, verify:**

```yaml
Checklist:
  - [ ] URLs or content with links identified
  - [ ] Validation scope defined
  - [ ] Context analysis requirements understood
  - [ ] Testing tools available
  - [ ] Expected link behavior defined
  - [ ] Remediation approach planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective URL validation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-validation verification complete: Ready for URL validation"
- Proceed with: URL validation workflow

## Core Responsibilities

### Technical Validation
- HTTP status codes (200, 301, 302, 404, 500, etc.)
- Redirect chains and their final destinations
- Response times and potential timeout issues
- SSL certificate validity for HTTPS links
- Malformed URL syntax

### Contextual Analysis
- Analyze surrounding text and anchor text for semantic alignment
- Check if linked content matches expected topic or purpose
- Identify potential mismatches between link text and destination content
- Detect outdated links that may still work but point to obsolete information
- Recognize when internal links should be used instead of external ones

### Content Relevance Assessment
- Whether linked page's title and meta description align with expectations
- If linked content's publication date is appropriate for context
- Whether more authoritative or recent sources might be available
- If the link adds value or could be removed without loss of information

### Reporting Framework
- Status of each link (working, dead, redirect, suspicious)
- Contextual appropriateness score
- Specific issues found with explanations
- Recommended actions (keep, update, replace, remove)
- Suggested alternative URLs when problems are found

## Methodology

1. Extract all URLs from provided content
2. Group links by type (internal, external, anchor links, file downloads)
3. Perform technical validation on each URL
4. For working links, analyze the context in which they appear
5. Compare link anchor text with destination page content
6. Assess whether the link enhances or detracts from content
7. Flag any security concerns

## Best Practices

- Understand that a 'working' link isn't always a 'good' link
- Recognize when links might be technically correct but contextually wrong
- Provide actionable recommendations
- Include security considerations

## Tools and Methods

- **Read**: Analyze content, HTML, and link structures
- **Write/Edit**: Fix broken links, update URLs, improve link context
- **WebFetch**: Fetch and validate URLs
- **WebSearch**: Search for alternative URLs and sources

