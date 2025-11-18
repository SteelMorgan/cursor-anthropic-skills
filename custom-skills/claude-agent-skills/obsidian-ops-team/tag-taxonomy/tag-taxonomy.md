---
name: tag-taxonomy
description: Obsidian tag taxonomy specialist. Use PROACTIVELY for normalizing and hierarchically organizing tag taxonomy, consolidating duplicates, and maintaining consistent tagging.
enforcement_level: MEDIUM
violation_consequence: Tags may be inconsistent, duplicates may exist, or taxonomy may be poorly organized, leading to poor content discoverability
---

# Tag Taxonomy

This skill provides comprehensive guidance for maintaining a clean, hierarchical, and consistent tag taxonomy across the vault.

## Overview

Tag taxonomy management involves normalizing tags, applying hierarchical structure, and consolidating duplicates. This skill provides systematic approaches to tag taxonomy as a Tag Standardization Agent.

## ✓ Pre-Standardization Checklist

**BEFORE standardizing tags, verify:**

```yaml
Checklist:
  - [ ] Vault location identified
  - [ ] Tag taxonomy document available
  - [ ] Standardization objectives defined
  - [ ] Scripts available
  - [ ] Backup created
  - [ ] Review process planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective tag standardization
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-standardization verification complete: Ready to standardize tags"
- Proceed with: Tag standardization workflow

## Core Responsibilities

1. **Normalize Technology Names**: Ensure consistent naming (e.g., "langchain" → "LangChain")
2. **Apply Hierarchical Structure**: Organize tags in parent/child relationships
3. **Consolidate Duplicates**: Merge similar tags (e.g., "ai-agents" and "ai/agents")
4. **Generate Analysis Reports**: Document tag usage and inconsistencies
5. **Maintain Tag Taxonomy**: Keep master taxonomy document updated

## Tag Hierarchy Standards

Follow hierarchical taxonomy structure:
- ai/agents/, ai/embeddings/, ai/llm/anthropic/, ai/frameworks/langchain/
- business/client-work/, business/strategy/
- development/python/, development/javascript/

## Workflow

1. Generate tag analysis report
2. Review tag usage and inconsistencies
3. Apply standardization based on taxonomy
4. Update master taxonomy document
5. Verify standardization results

## Best Practices

- Follow taxonomy hierarchy strictly
- Normalize technology names consistently
- Consolidate duplicates systematically
- Generate reports before changes
- Maintain taxonomy document updated

## Tools and Methods

- **Read**: Analyze tags and taxonomy documents
- **MultiEdit**: Update tags across multiple files
- **Bash**: Execute tag standardization scripts
- **Glob**: Find files with specific tags

