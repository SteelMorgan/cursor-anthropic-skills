---
name: connection-management
description: Obsidian vault connection specialist. Use PROACTIVELY for analyzing and suggesting links between related content, identifying orphaned notes, and creating knowledge graph connections.
enforcement_level: MEDIUM
violation_consequence: Notes may remain unconnected, knowledge graph may be incomplete, or relationships may be missed, leading to poor knowledge discovery
---

# Connection Management

This skill provides comprehensive guidance for identifying and suggesting meaningful connections between notes, creating a rich knowledge graph.

## Overview

Connection management involves finding relationships between notes, identifying orphaned content, and creating knowledge graph connections. This skill provides systematic approaches to connection management as a Connection Discovery Agent.

## ✓ Pre-Analysis Checklist

**BEFORE analyzing connections, verify:**

```yaml
Checklist:
  - [ ] Vault location identified
  - [ ] Connection objectives defined
  - [ ] Analysis scope determined
  - [ ] Scripts available
  - [ ] Output format planned
  - [ ] Review process established

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective connection analysis
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-analysis verification complete: Ready to analyze connections"
- Proceed with: Connection analysis workflow

## Core Responsibilities

1. **Entity-Based Connections**: Find notes mentioning same people, projects, technologies
2. **Keyword Overlap Analysis**: Identify notes with similar terminology and concepts
3. **Orphaned Note Detection**: Find notes with no incoming or outgoing links
4. **Link Suggestion Generation**: Create actionable reports for manual curation
5. **Connection Pattern Analysis**: Identify clusters and potential knowledge gaps

## Connection Strategies

1. **Entity Extraction**: People names, technologies, companies, projects
2. **Semantic Similarity**: Common technical terms, shared tags, similar directories
3. **Structural Analysis**: Notes in same directory, MOC relationships, daily notes references

## Workflow

1. Run link discovery script
2. Analyze entity mentions and keyword overlap
3. Identify orphaned notes
4. Generate link suggestions report
5. Review and curate connections

## Best Practices

- Focus on meaningful relationships
- Identify orphaned notes systematically
- Generate actionable suggestions
- Maintain knowledge graph quality
- Review suggestions before implementation

## Tools and Methods

- **Read**: Analyze notes and vault structure
- **Grep**: Search for entity mentions and keywords
- **Bash**: Execute connection discovery scripts
- **Write**: Create link suggestions and reports
- **Glob**: Find notes by patterns

