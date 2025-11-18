---
name: test-automation
description: This skill provides expertise in test automation and quality assurance. This skill should be used for test strategy, test automation, coverage analysis, CI/CD testing, or quality engineering practices. Focuses on maintainable, reliable tests with fast feedback.
enforcement_level: HIGH
violation_consequence: Test coverage may be insufficient, tests may be unreliable, or quality gates may fail, leading to production issues
---

# Test Automation

This skill provides comprehensive guidance for test automation, quality assurance, and testing strategies across all application layers. It emphasizes maintainable, reliable tests with fast feedback.

## Overview

Test automation involves creating comprehensive test suites that validate functionality, ensure quality, and provide fast feedback. This skill provides systematic approaches to test strategy and automation.

## ✓ Pre-Testing Checklist

**BEFORE creating test automation, verify:**

```yaml
Checklist:
  - [ ] Testing strategy defined
  - [ ] Test pyramid approach determined
  - [ ] Coverage thresholds established
  - [ ] Test tools and frameworks selected
  - [ ] CI/CD integration planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective test automation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-testing verification complete: Ready to create tests"
- Proceed with: Test automation workflow

## Core Testing Framework

### Testing Strategy

- **Test Pyramid**: Unit tests (70%), Integration tests (20%), E2E tests (10%)
- **Testing Types**: Functional, non-functional, regression, smoke, performance
- **Quality Gates**: Coverage thresholds, performance benchmarks, security checks
- **Risk Assessment**: Critical path identification, failure impact analysis
- **Test Data Management**: Test data generation, environment management

### Automation Architecture

- **Unit Testing**: Jest, Mocha, Vitest, pytest, JUnit
- **Integration Testing**: API testing, database testing, service integration
- **E2E Testing**: Playwright, Cypress, Selenium, Puppeteer
- **Visual Testing**: Screenshot comparison, UI regression testing
- **Performance Testing**: Load testing, stress testing, benchmark testing

## Test Organization

### Test Structure

- Organize tests by feature/component
- Use descriptive test names
- Follow Arrange-Act-Assert pattern
- Group related tests with describe blocks
- Keep tests independent and isolated

### Test Patterns

- **Page Object Model** for E2E tests
- **Test Data Factories** for data generation
- **Mock Services** for external dependencies
- **Database Helpers** for test data management
- **API Helpers** for API testing

### Test Pattern Examples

#### Page Object Model
```javascript
// Create page object for E2E tests
class TestPatterns {
  static createPageObject(page, selectors) {
    const pageObject = {};
    Object.entries(selectors).forEach(([name, selector]) => {
      pageObject[name] = {
        element: () => page.locator(selector),
        click: () => page.click(selector),
        fill: (text) => page.fill(selector, text),
        getText: () => page.textContent(selector),
        isVisible: () => page.isVisible(selector)
      };
    });
    return pageObject;
  }
}
```

#### Test Data Factory
```javascript
// Test data factory for generating test data
static createTestDataFactory(schema) {
  return {
    build: (overrides = {}) => {
      const data = {};
      Object.entries(schema).forEach(([key, generator]) => {
        data[key] = overrides[key] !== undefined 
          ? overrides[key] 
          : (typeof generator === 'function' ? generator() : generator);
      });
      return data;
    },
    buildList: (count, overrides = {}) => {
      return Array.from({ length: count }, (_, index) => 
        this.build({ ...overrides, id: index + 1 })
      );
    }
  };
}
```

#### Database Test Helpers
```javascript
// Database test helpers for test data management
static createDatabaseTestHelpers(db) {
  return {
    async cleanTables(tableNames) {
      for (const tableName of tableNames) {
        await db.query(`TRUNCATE TABLE ${tableName} RESTART IDENTITY CASCADE`);
      }
    },
    async seedTable(tableName, data) {
      if (Array.isArray(data)) {
        for (const row of data) {
          await db.query(`INSERT INTO ${tableName} (...) VALUES (...)`, Object.values(row));
        }
      } else {
        await db.query(`INSERT INTO ${tableName} (...) VALUES (...)`, Object.values(data));
      }
    }
  };
}
```

## CI/CD Integration

- Integrate tests into CI/CD pipeline
- Set up quality gates
- Configure test reporting
- Implement test result notifications
- Track test metrics over time

## Best Practices

- Create maintainable, reliable tests
- Provide fast feedback
- Achieve high confidence in code quality
- Follow test pyramid approach
- Use appropriate test types for each layer
- Maintain test data and environments

## Common Mistakes to Avoid

- ❌ Too many E2E tests
- ❌ Brittle tests that break frequently
- ❌ Tests that don't test anything meaningful
- ❌ Missing test coverage
- ❌ Slow test execution
- ❌ Not maintaining tests

Your testing implementations should always include: test strategy, automation pipeline, performance testing, quality metrics, and maintenance strategies. Focus on creating maintainable, reliable tests that provide fast feedback and high confidence in code quality.

