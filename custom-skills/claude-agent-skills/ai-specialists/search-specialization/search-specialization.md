---
name: search-specialization
description: This skill provides expertise in web research using advanced search techniques and synthesis. This skill should be used for deep research, information gathering, trend analysis, competitive analysis, or fact-checking. Masters search operators, result filtering, and multi-source verification.
enforcement_level: MEDIUM
violation_consequence: Research may be incomplete, inaccurate, or miss critical information, leading to poor decision-making
---

# Search Specialization

This skill provides comprehensive guidance for finding and synthesizing information from the web using advanced search techniques, result filtering, and multi-source verification.

## Overview

Search specialization involves formulating optimized queries, evaluating result quality, synthesizing information across sources, and verifying facts. This skill provides systematic approaches to web research.

## ✓ Pre-Search Checklist

**BEFORE conducting research, verify:**

```yaml
Checklist:
  - [ ] Research objective clearly understood
  - [ ] Information needs identified
  - [ ] Search scope defined
  - [ ] Quality criteria established
  - [ ] Verification approach planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective research
- Next step: Clarify research objectives before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-search verification complete: Ready to research"
- Proceed with: Search workflow

## Focus Areas

### Advanced Search Query Formulation

- Use specific phrases in quotes for exact matches
- Exclude irrelevant terms with negative keywords
- Target specific timeframes for recent/historical data
- Formulate multiple query variations

### Domain-Specific Searching and Filtering

- `allowed_domains` for trusted sources
- `blocked_domains` to exclude unreliable sites
- Target specific sites for authoritative content
- Academic sources for research topics

### Result Quality Evaluation and Ranking

- Assess source credibility and authority
- Evaluate information recency and relevance
- Check for bias and perspective
- Verify factual claims

### Information Synthesis Across Sources

- Identify common themes and patterns
- Note contradictions and discrepancies
- Synthesize insights from multiple sources
- Build comprehensive understanding

### Fact Verification and Cross-Referencing

- Verify key facts across multiple sources
- Check original sources and citations
- Identify consensus vs. outliers
- Document verification process

### Historical and Trend Analysis

- Search across time periods
- Identify trends and patterns
- Compare historical vs. current information
- Track evolution of information

## Search Strategies

### Query Optimization

**Exact Phrases**:
- Use quotes: `"exact phrase"`
- Preserve word order and meaning

**Negative Keywords**:
- Exclude terms: `-unwanted -term`
- Filter out irrelevant results

**Time Targeting**:
- Recent: `after:2024-01-01`
- Historical: `before:2020-01-01`
- Specific period: `2020..2024`

**Query Variations**:
- Create 3-5 variations for coverage
- Test different phrasings
- Explore synonyms and related terms

### Domain Filtering

**Trusted Sources**:
- Academic: `.edu`, `.ac.uk`
- Government: `.gov`, `.gov.uk`
- Organizations: `.org`
- Specific domains: `site:example.com`

**Blocked Domains**:
- Exclude unreliable sites
- Filter out spam and low-quality content
- Remove biased or untrustworthy sources

### WebFetch Deep Dive

- Extract full content from promising results
- Parse structured data from pages
- Follow citation trails and references
- Capture data before it changes

## Approach

Follow this systematic approach:

1. **Understand the research objective clearly**
   - Define what information is needed
   - Identify success criteria
   - Determine scope and depth

2. **Create 3-5 query variations for coverage**
   - Different phrasings
   - Synonyms and related terms
   - Varying specificity levels

3. **Search broadly first, then refine**
   - Start with broad queries
   - Narrow based on results
   - Iterate and refine

4. **Verify key facts across multiple sources**
   - Cross-reference important claims
   - Check original sources
   - Identify consensus

5. **Track contradictions and consensus**
   - Note disagreements
   - Identify common themes
   - Document verification

## Output Format

Provide:

### Research Methodology

- Queries used and rationale
- Sources consulted
- Search strategy employed
- Verification approach

### Curated Findings

- Key insights with source URLs
- Important facts and data points
- Trends and patterns identified
- Contradictions or gaps noted

### Credibility Assessment

- Source credibility evaluation
- Information quality assessment
- Bias and perspective analysis
- Reliability indicators

### Synthesis

- Key insights highlighted
- Common themes identified
- Contradictions explained
- Comprehensive understanding built

### Data Tables or Structured Summaries

- Organized information
- Comparative data
- Trend analysis
- Summary statistics

### Recommendations for Further Research

- Additional areas to explore
- Unanswered questions
- Suggested next steps
- Related topics

## Best Practices

- Start with clear research objectives
- Use multiple query variations
- Verify facts across sources
- Document sources and methodology
- Synthesize insights, don't just list facts
- Provide actionable insights

## Common Mistakes to Avoid

- ❌ Using only one query
- ❌ Not verifying facts
- ❌ Ignoring source credibility
- ❌ Missing contradictions
- ❌ Not synthesizing information
- ❌ Providing only URLs without context

Focus on actionable insights. Always provide direct quotes for important claims. Ensure research is thorough, accurate, and well-synthesized.

