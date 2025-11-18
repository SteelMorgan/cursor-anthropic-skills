---
name: dependency-management
description: Use this skill to manage project dependencies. Specializes in dependency analysis, vulnerability scanning, and license compliance.
enforcement_level: HIGH
violation_consequence: Dependencies may be outdated, vulnerable, or non-compliant, leading to security risks, compatibility issues, or legal problems
---

# Dependency Management

This skill provides comprehensive guidance for managing project dependencies, including analysis, updates, vulnerability scanning, and license compliance.

## Overview

Dependency management involves ensuring project dependencies are up-to-date, secure, and compliant with licensing requirements. This skill provides systematic approaches to dependency management as a Dependency Manager expert specializing in software composition analysis.

## ✓ Pre-Management Checklist

**BEFORE managing dependencies, verify:**

```yaml
Checklist:
  - [ ] Package manager and project type identified
  - [ ] Current dependency versions documented
  - [ ] Update strategy determined
  - [ ] Test suite available for validation
  - [ ] License requirements understood
  - [ ] Security policies defined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective dependency management
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-management verification complete: Ready to manage dependencies"
- Proceed with: Dependency management workflow

## Core Expertise Areas

- **Dependency Analysis**: Identifying unused dependencies, resolving version conflicts, and optimizing the dependency tree
- **Vulnerability Scanning**: Using tools like `npm audit`, `pip-audit`, or `trivy` to find and fix known vulnerabilities in dependencies
- **License Compliance**: Verifying that all dependency licenses are compatible with the project's license and policies
- **Dependency Updates**: Safely updating dependencies to their latest secure versions

## When to Use This Skill

Use this skill for:
- Updating project dependencies
- Checking for security vulnerabilities in dependencies
- Analyzing and optimizing the project's dependency tree
- Ensuring license compliance

## Dependency Management Process

1. **Analyze dependencies**: Use the appropriate package manager to list all dependencies and their versions
2. **Scan for vulnerabilities**: Run a vulnerability scan on the dependencies
3. **Check for updates**: Identify outdated dependencies and their latest versions
4. **Update dependencies**: Update dependencies in a safe and controlled manner, running tests after each update
5. **Verify license compliance**: Check the licenses of all dependencies

## Tools by Package Manager

### npm
- `npm outdated` - Check for outdated packages
- `npm update` - Update packages
- `npm audit` - Security vulnerability audit
- `npm audit fix` - Fix vulnerabilities automatically

### yarn
- `yarn outdated` - Check for outdated packages
- `yarn upgrade` - Update packages
- `yarn audit` - Security vulnerability audit

### pip
- `pip list --outdated` - Check for outdated packages
- `pip install -U` - Update packages
- `pip-audit` - Security vulnerability audit

### maven
- `mvn versions:display-dependency-updates` - Check for updates
- `mvn versions:use-latest-versions` - Update versions

### gradle
- `gradle dependencyUpdates` - Check for dependency updates

## Output Format

Provide a structured report with:
- **Vulnerability Report**: A list of vulnerabilities found, with their severity and recommended actions
- **Update Report**: A list of dependencies that were updated, with their old and new versions
- **License Report**: A summary of the licenses used in the project and any potential conflicts

## Vulnerability Severity Levels

- **Critical**: Immediate action required, potential for severe impact
- **High**: Should be addressed soon, significant impact possible
- **Medium**: Should be addressed when possible, moderate impact
- **Low**: Can be addressed in future updates, minimal impact

## Update Strategy

### Major Version Updates
- Review changelog for breaking changes
- Test thoroughly after update
- Update code if necessary for compatibility

### Minor/Patch Updates
- Generally safe to update
- Run tests to verify compatibility
- Monitor for any issues

## License Compliance

### Common License Types
- **MIT**: Permissive, compatible with most projects
- **Apache 2.0**: Permissive, requires attribution
- **GPL**: Copyleft, requires derivative works to be GPL
- **BSD**: Permissive, similar to MIT

### License Compatibility Checklist
- [ ] All dependencies have compatible licenses
- [ ] License requirements are documented
- [ ] Attribution requirements are met
- [ ] No conflicting license obligations

## Best Practices

- Update dependencies regularly to stay current
- Test thoroughly after updates
- Use lock files to ensure reproducible builds
- Monitor for security vulnerabilities
- Document license requirements
- Keep dependencies minimal and necessary
- Remove unused dependencies

## Tools and Methods

- **Read**: Analyze package.json, requirements.txt, and dependency files
- **Write/Edit**: Update dependency versions and configuration files
- **Bash**: Run package manager commands, vulnerability scans, and tests

