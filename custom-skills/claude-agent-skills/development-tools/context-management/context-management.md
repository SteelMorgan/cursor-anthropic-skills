---
name: context-management
description: This skill provides expertise in context management for multi-agent workflows and long-running tasks. This skill should be used for complex projects, session coordination, or when context preservation is needed across multiple agents. Focuses on efficient context compression and distribution.
enforcement_level: MEDIUM
violation_consequence: Context may be lost or inefficiently managed, leading to redundant work or incomplete understanding across sessions
---

# Context Management

This skill provides comprehensive guidance for maintaining coherent state across multiple agent interactions and sessions. It ensures efficient context capture, distribution, and memory management for complex, long-running projects.

## Overview

Context management involves capturing key decisions, distributing relevant context to agents, and maintaining memory across sessions. This skill provides systematic approaches to context optimization and preservation.

## ✓ Pre-Context Checklist

**BEFORE managing context, verify:**

```yaml
Checklist:
  - [ ] Current conversation and agent outputs reviewed
  - [ ] Important decisions and rationale identified
  - [ ] Context distribution needs understood
  - [ ] Memory storage requirements determined
  - [ ] Context compression strategy planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective context management
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-context verification complete: Ready to manage context"
- Proceed with: Context management workflow

## Core Functions

### 1. Context Capture

Extract and store:
- Key decisions and rationale from agent outputs
- Reusable patterns and solutions
- Integration points between components
- Unresolved issues and TODOs
- Critical project information

### 2. Context Distribution

Prepare and deliver:
- Minimal, relevant context for each agent
- Agent-specific briefings
- Context index for quick retrieval
- Pruned outdated or irrelevant information

### 3. Memory Management

Store and maintain:
- Critical project decisions in memory
- Rolling summary of recent changes
- Index of commonly accessed information
- Context checkpoints at major milestones

## Workflow Integration

When activated:

1. **Review** the current conversation and agent outputs
2. **Extract** and store important context
3. **Create** a summary for the next agent/session
4. **Update** the project's context index
5. **Suggest** when full context compression is needed

## Context Formats

### Quick Context (< 500 tokens)

Include:
- Current task and immediate goals
- Recent decisions affecting current work
- Active blockers or dependencies

### Full Context (< 2000 tokens)

Include:
- Project architecture overview
- Key design decisions
- Integration points and APIs
- Active work streams

### Archived Context (stored in memory)

Store:
- Historical decisions with rationale
- Resolved issues and solutions
- Pattern library
- Performance benchmarks

## Best Practices

- Optimize for relevance over completeness
- Good context accelerates work; bad context creates confusion
- Extract key decisions, not all details
- Maintain context index for quick retrieval
- Prune outdated information regularly
- Create checkpoints at major milestones

## Common Mistakes to Avoid

- ❌ Including too much irrelevant context
- ❌ Not capturing key decisions
- ❌ Failing to update context index
- ❌ Not pruning outdated information
- ❌ Missing context checkpoints

Always optimize for relevance over completeness. Good context accelerates work; bad context creates confusion.

