---
name: flutter-go-review
description: This skill provides expertise in code review for backend (Golang/Protobuf/Postgres) and frontend (Flutter/Riverpod/GetX) code. This skill should be used when reviewing code changes in pull requests or after writing/modifying code. Categorizes findings as Critical Issues, Suggestions, or Praise.
enforcement_level: HIGH
violation_consequence: Code quality issues may remain undetected, leading to bugs, security vulnerabilities, or maintainability problems
---

# Flutter/Go Code Review

This skill provides comprehensive guidance for reviewing backend (Golang, Protobuf, PostgreSQL) and frontend (Flutter, Riverpod, GetX) code. It ensures high quality, maintainability, and operational safety.

## Overview

Code review involves systematically examining code changes to identify issues, suggest improvements, and ensure adherence to team standards. This skill provides structured approaches to reviewing Go and Flutter codebases.

## ✓ Pre-Review Checklist

**BEFORE starting code review, verify:**

```yaml
Checklist:
  - [ ] Code changes identified and accessible
  - [ ] Review scope defined
  - [ ] Team standards understood
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

## Review Framework

For every code review, categorize findings into three types:

- **🔴 Critical Issue**: Must be fixed before merge (blocks deployment)
- **🟡 Suggestion**: Improvement opportunity (not blocking)
- **🟢 Praise**: Recognition for excellent code practices

Always provide specific examples and line references when identifying issues.

## Review Checklist

### 1. Code Quality

**Readability**
- Verify code is clean, self-explanatory, and follows consistent style
- Check variable/function/struct/class names are descriptive and meaningful
- Flag clever hacks that reduce clarity

**Small & Simple Functions**
- Ensure functions are under 30 lines and single-purpose
- Check for minimal nesting (max 3 levels) and clear control flow
- Identify opportunities to split complex functions

**Comments & Documentation**
- Verify comments explain 'why' not 'what'
- Ensure public APIs have proper docstrings
- Check complex algorithms have explanatory comments

**Modularization**
- Verify proper organization into structs/methods (avoid scattered helpers)
- Check for appropriate code reuse and DRY principles
- Ensure proper layering (UI → Service → DB)

### 2. Testing

- Verify new/changed logic has unit test coverage
- Check edge cases and error paths are tested
- Ensure bug fixes include regression tests
- Flag if PR reduces overall test coverage
- Verify integration tests for new external dependencies

### 3. Feature Protection

**Backward Compatibility**
- Check API changes maintain backward compatibility
- Verify database migrations support zero-downtime deployment
- Flag breaking changes that lack versioning strategy

**Feature Flags**
- Ensure new features are behind feature flags
- Verify flags have documented removal paths
- Check no behavior changes occur without toggles

### 4. Operational Safety

- Verify critical paths have appropriate logging (without sensitive data)
- Check all errors are handled explicitly (no silent failures)
- Ensure monitoring/metrics hooks are updated for new features
- Verify graceful degradation for external service failures

### 5. Security & Performance

- Flag any hardcoded secrets or credentials
- Check for SQL injection vulnerabilities
- Review query efficiency and potential N+1 problems
- Verify proper input validation and sanitization
- Check for memory leaks or inefficient loops

### 6. Platform-Specific Guidelines

**Backend (Golang + Protobuf + PostgreSQL)**
- Protobuf changes: Verify backward compatibility, check field documentation
- Database: Ensure schema.sql changes have migrations, verify query safety
- Code structure: Verify business logic in structs/methods, check package boundaries

**Frontend (Flutter + Riverpod + GetX)**
- State Management: Verify correct Riverpod usage, check GetX localization
- Component Structure: Ensure proper widget modularization, verify reusability

## Review Process

1. Start with a high-level assessment of the change's purpose and scope
2. Review files in logical order (interfaces → implementation → tests)
3. For each finding:
   - Quote the specific code
   - Explain the issue clearly
   - Provide a concrete fix or improvement
   - Categorize appropriately (Critical/Suggestion/Praise)
4. End with a summary including:
   - Count of each finding type
   - Overall assessment
   - Merge recommendation (Ready/Needs Changes/Needs Discussion)

## Communication Style

- Be specific and actionable in all feedback
- Explain the 'why' behind each issue (impact on users/system/team)
- Balance criticism with recognition of good practices
- Use respectful, constructive language
- Provide code examples for suggested improvements
- Ask clarifying questions when intent is unclear

## Special Attention Areas

**Flag for human review**:
- Major architectural changes
- Security-sensitive code
- Business logic modifications
- Performance-critical paths
- Complex state management changes
- Database schema changes affecting core entities

## Best Practices

- Improve code quality while maintaining team velocity
- Be thorough but pragmatic
- Focus on issues that truly matter for system reliability, maintainability, and user experience
- Provide specific examples and line references
- Balance criticism with recognition

Remember: Your goal is to improve code quality while maintaining team velocity. Be thorough but pragmatic, focusing on issues that truly matter for system reliability, maintainability, and user experience.

