---
name: query-clarification
description: Analyze research queries for clarity and determine if user clarification is needed before proceeding with research. Use PROACTIVELY at the beginning of research workflows to ensure queries are specific and actionable.
enforcement_level: HIGH
violation_consequence: Research may proceed with ambiguous queries, leading to incomplete or incorrect results, wasted resources, or missed objectives
---

# Query Clarification

This skill provides comprehensive guidance for analyzing research queries to ensure they are clear, specific, and actionable before research begins.

## Overview

Query clarification involves analyzing research queries for ambiguity, vagueness, and missing context to ensure research quality. This skill provides systematic approaches to query clarification as a Query Clarifier expert in analyzing research queries.

## ✓ Pre-Clarification Checklist

**BEFORE clarifying queries, verify:**

```yaml
Checklist:
  - [ ] Research query received
  - [ ] Analysis framework ready
  - [ ] Clarification criteria established
  - [ ] Output format defined
  - [ ] Decision framework applied
  - [ ] Communication approach planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective query clarification
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-clarification verification complete: Ready to clarify query"
- Proceed with: Query clarification workflow

## Analysis Dimensions

1. **Ambiguity or vagueness**: Terms that could mean multiple things or lack specificity
2. **Multiple interpretations**: Queries that could reasonably be understood in different ways
3. **Missing context or scope**: Lack of boundaries, timeframes, domains, or specific use cases
4. **Unclear objectives**: Uncertain what the user wants to achieve or learn
5. **Overly broad topics**: Subjects too vast to research effectively without focus

## Decision Framework

- **Proceed without clarification** (confidence > 0.8): Query has clear intent, specific scope, and actionable objectives
- **Refine and proceed** (confidence 0.6-0.8): Minor ambiguities exist but core intent is apparent; can reasonably infer missing details
- **Request clarification** (confidence < 0.6): Significant ambiguity, multiple valid interpretations, or critical missing information

## Clarification Questions Guidelines

- Limit to 1-3 most critical questions
- Prefer yes/no or multiple choice formats
- Make each question specific and directly tied to improving research
- Explain briefly why each clarification matters
- Avoid overwhelming users with too many questions

## Output Format

Provide structured JSON with:
- needs_clarification (boolean)
- confidence_score (0.0-1.0)
- analysis (explanation of decision)
- questions (clarification questions if needed)
- refined_query (clarified version)
- focus_areas (specific aspects)

## Best Practices

- Analyze queries systematically
- Identify ambiguities early
- Request only critical clarifications
- Provide clear reasoning
- Refine queries when possible

## Tools and Methods

- **Read**: Analyze research queries
- **Write/Edit**: Create clarification requests and refined queries

