---
name: changelog-generation
description: Changelog and release notes specialist. Use PROACTIVELY for generating changelogs from git history, creating release notes, and maintaining version documentation.
enforcement_level: MEDIUM
violation_consequence: Changelogs may be incomplete, inconsistent, or difficult to understand, leading to confusion about changes and version history
---

# Changelog Generation

This skill provides comprehensive guidance for creating clear, structured changelogs and release notes that communicate changes effectively to users.

## Overview

Changelog generation involves creating clear documentation of changes, releases, and version history. This skill provides systematic approaches to changelog creation as a changelog and release documentation specialist focused on clear communication of changes.

## ✓ Pre-Generation Checklist

**BEFORE generating changelog, verify:**

```yaml
Checklist:
  - [ ] Git history accessible and analyzed
  - [ ] Commit messages follow conventions
  - [ ] Version numbers determined
  - [ ] Release date identified
  - [ ] Breaking changes identified
  - [ ] Categorization strategy defined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective changelog generation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-generation verification complete: Ready to generate changelog"
- Proceed with: Changelog generation workflow

## Focus Areas

- **Automated changelog generation** from git commits
- **Release notes** with user-facing impact
- **Version migration guides** and breaking changes
- **Semantic versioning** and release planning
- **Change categorization** and audience targeting
- **Integration with CI/CD** and release workflows

## Approach

1. **Follow Conventional Commits** for parsing
2. **Categorize changes** by user impact
3. **Lead with breaking changes** and migrations
4. **Include upgrade instructions** and examples
5. **Link to relevant documentation** and issues
6. **Automate generation** but curate content

## Output Deliverables

### CHANGELOG.md (Keep a Changelog Format)
```markdown
# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

## [1.0.0] - 2024-01-15

### Added
- New feature descriptions

### Changed
- Changes to existing functionality

### Deprecated
- Soon-to-be removed features

### Removed
- Removed features

### Fixed
- Bug fixes

### Security
- Security fixes
```

### Release Notes
- User-facing highlights
- Download links and version information
- Migration instructions
- Breaking changes prominently featured
- Links to documentation and issues

### Migration Guides
- Step-by-step upgrade instructions
- Breaking change explanations
- Code examples showing before/after
- Common issues and solutions
- Rollback procedures

### Automated Generation Scripts
- Git commit parsing
- Conventional Commits support
- Categorization logic
- Formatting and templating
- CI/CD integration

### Commit Message Conventions
- Conventional Commits format
- Commit message templates
- Examples and guidelines
- Tooling recommendations

### Release Workflow Documentation
- Release process steps
- Version numbering strategy
- Testing procedures
- Deployment checklist

## Change Categorization

Group changes by impact:
- **Breaking**: Changes that require user action
- **Features**: New functionality
- **Fixes**: Bug fixes and improvements
- **Internal**: Developer-facing changes

## Best Practices

- Include dates and version links
- Use consistent formatting
- Provide context for changes
- Link to related issues and PRs
- Highlight breaking changes prominently
- Include migration instructions
- Test all examples and instructions
- Keep changelog up-to-date

## Tools and Methods

- **Read**: Analyze git history, commit messages, and existing changelogs
- **Write/Edit**: Create changelog files, release notes, and migration guides
- **Bash**: Generate changelogs from git, automate release processes

## Semantic Versioning

Follow semantic versioning (MAJOR.MINOR.PATCH):
- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes (backward compatible)

## Common Patterns

### Conventional Commits Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

Types: feat, fix, docs, style, refactor, test, chore, breaking

### Changelog Entry Format
- Clear, concise descriptions
- User-focused language
- Links to related issues
- Examples when helpful
- Migration notes for breaking changes

