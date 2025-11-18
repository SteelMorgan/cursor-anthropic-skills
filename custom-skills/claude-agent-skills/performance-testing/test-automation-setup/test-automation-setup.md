---
name: test-automation-setup
description: Create comprehensive test suites with unit, integration, and e2e tests. Sets up CI pipelines, mocking strategies, and test data. Use PROACTIVELY for test coverage improvement or test automation setup.
enforcement_level: HIGH
violation_consequence: Test suites may be incomplete, unreliable, or poorly configured, leading to insufficient test coverage and quality issues
---

# Test Automation Setup

This skill provides comprehensive guidance for creating test suites, setting up CI pipelines, and implementing test automation strategies.

## Overview

Test automation setup involves creating comprehensive test suites with proper structure, CI/CD integration, and test data management. This skill provides systematic approaches to test automation setup as a test automation specialist focused on comprehensive testing strategies.

## ✓ Pre-Setup Checklist

**BEFORE setting up test automation, verify:**

```yaml
Checklist:
  - [ ] Testing strategy defined
  - [ ] Test frameworks selected
  - [ ] CI/CD pipeline planned
  - [ ] Test data strategy determined
  - [ ] Coverage goals established
  - [ ] Test environment configured

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective test automation setup
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-setup verification complete: Ready to set up test automation"
- Proceed with: Test automation setup workflow

## Focus Areas

- **Unit test design** with mocking and fixtures
- **Integration tests** with test containers
- **E2E tests** with Playwright/Cypress
- **CI/CD test pipeline** configuration
- **Test data management** and factories
- **Coverage analysis** and reporting

## Approach

1. Test pyramid - many unit, fewer integration, minimal E2E
2. Arrange-Act-Assert pattern
3. Test behavior, not implementation
4. Deterministic tests - no flakiness
5. Fast feedback - parallelize when possible

## Output Deliverables

- Test suite with clear test names
- Mock/stub implementations for dependencies
- Test data factories or fixtures
- CI pipeline configuration for tests
- Coverage report setup
- E2E test scenarios for critical paths

## Best Practices

- Use appropriate testing frameworks (Jest, pytest, etc.)
- Include both happy and edge cases
- Keep tests independent and isolated
- Use descriptive test names
- Maintain test data separately

## Tools and Methods

- **Read**: Analyze code, existing tests, and CI configurations
- **Write/Edit**: Create test suites, CI configurations, and test utilities
- **Bash**: Run tests, generate coverage reports, execute CI pipelines

