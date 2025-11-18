---
name: code-cleanup
description: This skill provides expertise in detecting and removing unused code across multiple languages. This skill should be used after refactoring, when removing features, or before production deployment. Focuses on safety over aggressive cleanup.
enforcement_level: MEDIUM
violation_consequence: Unused code may remain, or critical code may be accidentally removed, causing system failures
---

# Code Cleanup

This skill provides comprehensive guidance for static code analysis and safe dead code removal across multiple programming languages. It emphasizes safety and validation over aggressive cleanup.

## Overview

Code cleanup involves identifying unused imports, functions, and classes, then safely removing them while preserving critical code. This skill provides systematic approaches to dead code detection and removal.

## ✓ Pre-Cleanup Checklist

**BEFORE cleaning up code, verify:**

```yaml
Checklist:
  - [ ] Project languages and structure identified
  - [ ] Entry points and critical paths mapped
  - [ ] Dependency graph and usage patterns built
  - [ ] Dynamic usage patterns checked
  - [ ] Framework patterns preserved
  - [ ] Backup created before changes

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for safe code cleanup
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-cleanup verification complete: Ready to cleanup"
- Proceed with: Code cleanup workflow

## Analysis Checklist

- □ Language detection completed
- □ Entry points identified
- □ Cross-file dependencies mapped
- □ Dynamic usage patterns checked
- □ Framework patterns preserved
- □ Backup created before changes
- □ Tests pass after each removal

## Core Detection Patterns

### Unused Imports

**Python**: AST-based analysis
- Track import statements vs actual usage
- Skip dynamic imports (importlib, __import__)

**JavaScript**: Module analysis
- Track import/require vs references
- Skip dynamic imports, lazy loading

### Unused Functions/Classes

- Define all declared functions/classes
- Reference direct calls, inheritance, callbacks
- Preserve entry points, framework hooks, event handlers

### Dynamic Usage Safety

Never remove if patterns detected:
- Python: `getattr()`, `eval()`, `globals()`
- JavaScript: `window[]`, `this[]`, dynamic `import()`
- Java: Reflection, annotations (`@Component`, `@Service`)

## Framework Preservation Rules

### Python
- Django: Models, migrations, admin registrations
- Flask: Routes, blueprints, app factories
- FastAPI: Endpoints, dependencies

### JavaScript
- React: Components, hooks, context providers
- Vue: Components, directives, mixins
- Angular: Decorators, services, modules

### Java
- Spring: Beans, controllers, repositories
- JPA: Entities, repositories

## Execution Process

### 1. Backup Creation

```bash
backup_dir="./unused_code_backup_$(date +%Y%m%d_%H%M%S)"
cp -r . "$backup_dir" 2>/dev/null || mkdir -p "$backup_dir" && rsync -a . "$backup_dir"
```

### 2. Language-Specific Analysis

```bash
# Python
find . -name "*.py" -type f | while read file; do
    python -m ast "$file" 2>/dev/null || echo "Syntax check: $file"
done

# JavaScript/TypeScript
npx depcheck  # For npm packages
npx ts-unused-exports tsconfig.json  # For TypeScript
```

### 3. Safe Removal Strategy

- Create temp file with change
- Validate syntax
- Run tests if available
- Apply or rollback

### 4. Validation Commands

```bash
# Python
python -m py_compile file.py
python -m pytest

# JavaScript
npx eslint file.js
npm test

# Java
javac -Xlint file.java
mvn test
```

## Entry Point Patterns

Always preserve:
- `main.py`, `__main__.py`, `app.py`, `run.py`
- `index.js`, `main.js`, `server.js`, `app.js`
- `Main.java`, `*Application.java`, `*Controller.java`
- Config files: `*.config.*`, `settings.*`, `setup.*`
- Test files: `test_*.py`, `*.test.js`, `*.spec.js`

## Report Format

For each operation provide:
- **Files analyzed**: Count and types
- **Unused detected**: Imports, functions, classes
- **Safely removed**: With validation status
- **Preserved**: Reason for keeping
- **Impact metrics**: Lines removed, size reduction

## Safety Guidelines

✅ **Do:**
- Run tests after each removal
- Preserve framework patterns
- Check string references in templates
- Validate syntax continuously
- Create comprehensive backups

❌ **Don't:**
- Remove without understanding purpose
- Batch remove without testing
- Ignore dynamic usage patterns
- Skip configuration files
- Remove from migrations

## Best Practices

- Focus on safety over aggressive cleanup
- When uncertain, preserve code and flag for manual review
- Validate after each removal
- Preserve framework-specific patterns
- Create backups before changes
- Test thoroughly after cleanup

Focus on safety over aggressive cleanup. When uncertain, preserve code and flag for manual review.

