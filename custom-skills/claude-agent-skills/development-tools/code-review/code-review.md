---
name: code-review
description: Expert code review specialist for quality, security, and maintainability. Use PROACTIVELY after writing or modifying code to ensure high development standards.
enforcement_level: HIGH
violation_consequence: Code quality may be poor, security vulnerabilities may be introduced, or code may be unmaintainable
---

# Code Review

This skill provides comprehensive guidance for ensuring high standards of code quality and security through systematic code review processes.

## Overview

Code review involves analyzing code changes for quality, security, and maintainability. This skill provides systematic approaches to code review as a senior code reviewer ensuring high standards.

## ✓ Pre-Review Checklist

**BEFORE starting code review, verify:**

```yaml
Checklist:
  - [ ] Recent changes identified (git diff available)
  - [ ] Modified files accessible
  - [ ] Review scope defined
  - [ ] Context of changes understood
  - [ ] Related files reviewed if needed

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing prerequisites for effective code review
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-review verification complete: Ready to review"
- Proceed with: Code review workflow

## Review Process

When invoked:
1. Run git diff to see recent changes
2. Focus on modified files
3. Begin review immediately

## Review Checklist

- Code is simple and readable
- Functions and variables are well-named
- No duplicated code
- Proper error handling
- No exposed secrets or API keys
- Input validation implemented
- Good test coverage
- Performance considerations addressed

## Feedback Organization

Provide feedback organized by priority:
- **Critical issues (must fix)**: Security vulnerabilities, bugs that will cause failures, exposed secrets
- **Warnings (should fix)**: Code quality issues, potential bugs, maintainability concerns
- **Suggestions (consider improving)**: Style improvements, optimization opportunities, best practices

## Tools and Methods

- **Read**: Analyze code files and changes
- **Write/Edit**: Suggest code improvements
- **Bash**: Run git diff and other commands
- **Grep**: Search for patterns, secrets, anti-patterns

## Best Practices

- Include specific examples of how to fix issues
- Reference specific line numbers and files
- Provide code examples for suggested improvements
- Explain the reasoning behind each recommendation
- Consider the context and impact of changes
