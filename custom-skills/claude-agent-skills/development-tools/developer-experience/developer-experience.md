---
name: developer-experience
description: This skill provides expertise in Developer Experience (DX) optimization for tooling, setup, and workflow improvement. This skill should be used when setting up projects, reducing friction, or improving development workflows and automation. Focuses on making development joyful and productive.
enforcement_level: MEDIUM
violation_consequence: Development workflows may be inefficient, onboarding may be slow, or developer productivity may be reduced
---

# Developer Experience

This skill provides comprehensive guidance for optimizing developer experience by reducing friction, automating repetitive tasks, and making development joyful and productive.

## Overview

Developer Experience optimization involves identifying pain points, automating repetitive tasks, and creating intuitive workflows that enhance productivity and satisfaction.

## ✓ Pre-Optimization Checklist

**BEFORE optimizing DX, verify:**

```yaml
Checklist:
  - [ ] Current developer workflows profiled
  - [ ] Pain points and time sinks identified
  - [ ] Best practices and tools researched
  - [ ] Improvement priorities determined
  - [ ] Success metrics defined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective DX optimization
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-optimization verification complete: Ready to optimize DX"
- Proceed with: DX optimization workflow

## Optimization Areas

### Environment Setup

Optimize:
- Simplify onboarding to < 5 minutes
- Create intelligent defaults
- Automate dependency installation
- Add helpful error messages

### Development Workflows

Improve:
- Identify repetitive tasks for automation
- Create useful aliases and shortcuts
- Optimize build and test times
- Improve hot reload and feedback loops

### Tooling Enhancement

Enhance:
- Configure IDE settings and extensions
- Set up git hooks for common checks
- Create project-specific CLI commands
- Integrate helpful development tools

### Documentation

Improve:
- Generate setup guides that actually work
- Create interactive examples
- Add inline help to custom commands
- Maintain up-to-date troubleshooting guides

## Analysis Process

1. **Profile** current developer workflows
2. **Identify** pain points and time sinks
3. **Research** best practices and tools
4. **Implement** improvements incrementally
5. **Measure** impact and iterate

## Deliverables

Provide:
- `.claude/commands/` additions for common tasks
- Improved `package.json` scripts
- Git hooks configuration
- IDE configuration files
- Makefile or task runner setup
- README improvements

## Success Metrics

Measure:
- Time from clone to running app
- Number of manual steps eliminated
- Build/test execution time
- Developer satisfaction feedback

## Best Practices

- Great DX is invisible when it works and obvious when it doesn't
- Aim for invisible, seamless experience
- Automate repetitive tasks
- Provide helpful error messages
- Create intuitive workflows
- Document clearly

## Common Mistakes to Avoid

- ❌ Over-complicating setup
- ❌ Not automating repetitive tasks
- ❌ Poor error messages
- ❌ Missing documentation
- ❌ Ignoring developer feedback

Remember: Great DX is invisible when it works and obvious when it doesn't. Aim for invisible.

