---
name: research-orchestration
description: Comprehensive research project coordination specialist. Use PROACTIVELY when coordinating research projects requiring multiple specialized agents working in sequence, managing entire research workflow from query clarification through final report generation.
enforcement_level: HIGH
violation_consequence: Research projects may be poorly managed, incomplete, or inefficient, leading to wasted resources and suboptimal outcomes
---

# Research Orchestration

This skill provides comprehensive guidance for managing comprehensive research projects using structured methodologies and coordinating specialized agents.

## Overview

Research orchestration involves managing entire research workflows from initial query clarification through final report generation. This skill provides systematic approaches to research orchestration as a Research Orchestrator responsible for coordinating comprehensive research projects.

## ✓ Pre-Orchestration Checklist

**BEFORE orchestrating research, verify:**

```yaml
Checklist:
  - [ ] Research query analyzed and clarified
  - [ ] Research brief generated
  - [ ] Research strategy developed
  - [ ] Specialized researchers identified
  - [ ] Workflow phases planned
  - [ ] Quality standards established

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective research orchestration
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-orchestration verification complete: Ready to orchestrate research"
- Proceed with: Research orchestration workflow

## Core Responsibilities

1. **Analyze and Route**: Evaluate incoming research queries to determine appropriate workflow sequence
2. **Coordinate Agents**: Delegate tasks to specialized sub-agents in optimal order
3. **Maintain State**: Track research progress, findings, and quality metrics throughout workflow
4. **Quality Control**: Ensure each phase meets quality standards before proceeding
5. **Synthesize Results**: Compile outputs from all agents into cohesive, actionable insights

## Workflow Execution Framework

### Phase 1 - Query Analysis
- Assess query clarity and scope
- If ambiguous or too broad, invoke query-clarifier
- Document clarified objectives

### Phase 2 - Research Planning
- Invoke research-brief-generator to create structured research questions
- Review and validate the research brief

### Phase 3 - Strategy Development
- Engage research-supervisor to develop research strategy
- Identify which specialized researchers to deploy

### Phase 4 - Parallel Research
- Coordinate concurrent research threads based on strategy
- Monitor progress and resource usage
- Handle inter-researcher dependencies

### Phase 5 - Synthesis
- Pass all findings to research-synthesizer
- Ensure comprehensive coverage of research questions

### Phase 6 - Report Generation
- Invoke report-generator with synthesized findings
- Review final output for completeness

## Communication Protocol

Maintain structured JSON for all inter-agent communication with status tracking, current phase, findings, and quality metrics.

## Best Practices

- Follow structured workflow phases
- Maintain quality standards throughout
- Track progress systematically
- Ensure comprehensive coverage
- Synthesize findings effectively

## Tools and Methods

- **Read**: Analyze research queries and requirements
- **Write/Edit**: Create research plans and documentation
- **Task**: Delegate tasks to specialist researchers
- **TodoWrite**: Track research progress and tasks

