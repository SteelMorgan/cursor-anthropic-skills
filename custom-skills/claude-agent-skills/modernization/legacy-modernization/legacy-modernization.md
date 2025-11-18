---
name: legacy-modernization
description: Refactor legacy codebases, migrate outdated frameworks, and implement gradual modernization. Handles technical debt, dependency updates, and backward compatibility. Use PROACTIVELY for legacy system updates, framework migrations, or technical debt reduction.
enforcement_level: HIGH
violation_consequence: Legacy modernization may break existing functionality, introduce bugs, or create migration blockers, requiring significant rollback and rework
---

# Legacy Modernization

This skill provides comprehensive guidance for safely refactoring legacy codebases, migrating outdated frameworks, and implementing gradual modernization while maintaining system stability.

## Overview

Legacy modernization involves safely upgrading legacy systems, migrating frameworks, and reducing technical debt. This skill provides systematic approaches to legacy modernization as a legacy modernization specialist focused on safe, incremental upgrades.

## ✓ Pre-Modernization Checklist

**BEFORE starting legacy modernization, verify:**

```yaml
Checklist:
  - [ ] Current system architecture understood
  - [ ] Legacy codebase analyzed
  - [ ] Framework migration path determined
  - [ ] Test coverage strategy planned
  - [ ] Backward compatibility requirements identified
  - [ ] Rollback procedures prepared

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective legacy modernization
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-modernization verification complete: Ready to modernize legacy system"
- Proceed with: Legacy modernization workflow

## Focus Areas

- **Framework migrations** (jQuery→React, Java 8→17, Python 2→3)
- **Database modernization** (stored procs→ORMs)
- **Monolith to microservices** decomposition
- **Dependency updates** and security patches
- **Test coverage** for legacy code
- **API versioning** and backward compatibility

## Approach

1. **Strangler fig pattern** - gradual replacement
2. **Add tests before refactoring**
3. **Maintain backward compatibility**
4. **Document breaking changes** clearly
5. **Feature flags** for gradual rollout

## Output Deliverables

### Migration Plan
- Phases and milestones
- Timeline and dependencies
- Risk assessment for each phase
- Success criteria and validation

### Refactored Code
- Modernized code with preserved functionality
- Improved structure and maintainability
- Updated dependencies and frameworks
- Performance optimizations

### Test Suite
- Tests for legacy behavior preservation
- Integration tests for compatibility
- Regression tests for critical paths
- Migration validation tests

### Compatibility Layers
- Adapter patterns for API compatibility
- Shim layers for gradual migration
- Wrapper functions for deprecated APIs
- Translation layers for data formats

### Deprecation Strategy
- Deprecation warnings and timelines
- Migration guides for users
- Breaking change documentation
- Support period definitions

### Rollback Procedures
- Rollback steps for each phase
- Data backup and restore procedures
- Configuration rollback steps
- Verification procedures after rollback

## Common Migration Scenarios

### Framework Migrations
- jQuery → React/Vue/Angular
- Java 8 → Java 17+
- Python 2 → Python 3
- AngularJS → Angular
- Backbone → Modern frameworks

### Database Modernization
- Stored procedures → ORMs
- Legacy databases → Modern databases
- SQL → NoSQL migrations
- Database schema modernization

### Dependency Updates
- Security patch application
- Major version upgrades
- Dependency consolidation
- License compliance updates

## Best Practices

- Focus on risk mitigation
- Never break existing functionality without migration path
- Add tests before refactoring
- Use feature flags for gradual rollout
- Maintain backward compatibility
- Document all changes clearly
- Test thoroughly at each phase

## Tools and Methods

- **Read**: Analyze legacy code, dependencies, and architecture
- **Write/Edit**: Create modernized code and migration scripts
- **Bash**: Run migration scripts, tests, and deployment
- **Grep**: Search for deprecated patterns and dependencies

## Risk Management

- Identify critical paths before changes
- Implement comprehensive testing
- Use feature flags for safe rollout
- Maintain rollback capabilities
- Monitor system health continuously
- Document all breaking changes

