---
name: research-brief-generation
description: Transform user's research query into structured, actionable research brief that guides subsequent research activities. Use PROACTIVELY when converting clarified queries into comprehensive research plans with specific questions, keywords, source preferences, and success criteria.
enforcement_level: HIGH
violation_consequence: Research briefs may be poorly structured, incomplete, or lack clear objectives, leading to inefficient research and incomplete findings
---

# Research Brief Generation

This skill provides comprehensive guidance for transforming user queries into comprehensive, structured research briefs that guide effective research execution.

## Overview

Research brief generation involves analyzing refined queries and creating actionable research briefs that break down complex questions into manageable, specific research objectives. This skill provides systematic approaches to research brief generation as a Research Brief Generator expert.

## ✓ Pre-Generation Checklist

**BEFORE generating research brief, verify:**

```yaml
Checklist:
  - [ ] Refined query available
  - [ ] Research objectives understood
  - [ ] Brief structure planned
  - [ ] Source strategy determined
  - [ ] Success criteria defined
  - [ ] Scope boundaries established

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective research brief generation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-generation verification complete: Ready to generate research brief"
- Proceed with: Research brief generation workflow

## Core Tasks

1. **Query Analysis**: Extract primary research objective, implicit assumptions, scope boundaries, expected outcome type
2. **Question Decomposition**: Transform main query into one clear main question and 3-5 specific sub-questions
3. **Keyword Engineering**: Generate primary terms, secondary terms, exclusion terms
4. **Source Strategy**: Determine optimal source distribution (academic, news, technical, data)
5. **Scope Definition**: Establish temporal, geographic, and depth boundaries
6. **Success Criteria**: Define what constitutes a complete answer

## Question Decomposition

- One clear, focused main research question (in first person)
- 3-5 specific sub-questions exploring different dimensions
- Each sub-question independently answerable
- Questions collectively provide comprehensive coverage

## Source Strategy

Determine optimal source distribution:
- **Academic** (0.0-1.0): Peer-reviewed papers, research studies
- **News** (0.0-1.0): Current events, recent developments
- **Technical** (0.0-1.0): Documentation, specifications, code
- **Data** (0.0-1.0): Statistics, datasets, empirical evidence

## Scope Definition

- **Temporal**: all, recent (last 2 years), historical (pre-2020), future (predictions/trends)
- **Geographic**: global, regional (specify), or specific locations
- **Depth**: overview (high-level), detailed (in-depth), comprehensive (exhaustive)

## Best Practices

- Break down complex questions systematically
- Create specific, actionable sub-questions
- Balance source types appropriately
- Define clear scope boundaries
- Establish measurable success criteria

## Tools and Methods

- **Read**: Analyze refined queries and requirements
- **Write/Edit**: Create structured research briefs

