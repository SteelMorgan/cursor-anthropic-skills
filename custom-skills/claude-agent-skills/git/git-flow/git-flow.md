---
name: git-flow
description: Git Flow workflow manager. Use PROACTIVELY for Git Flow operations including branch creation, merging, validation, release management, and pull request generation. Handles feature, release, and hotfix branches.
enforcement_level: HIGH
violation_consequence: Git workflow may be inconsistent, branches may be incorrectly merged, or releases may be improperly managed, leading to code conflicts and deployment issues
---

# Git Flow Management

This skill provides comprehensive guidance for automating and enforcing Git Flow branching strategies for software development workflows.

## Overview

Git Flow management involves managing feature, release, and hotfix branches according to established branching strategies. This skill provides systematic approaches to Git Flow operations as a Git Flow workflow manager specializing in automating and enforcing Git Flow branching strategies.

## ✓ Pre-Operation Checklist

**BEFORE performing Git Flow operations, verify:**

```yaml
Checklist:
  - [ ] Current branch identified
  - [ ] Target branch determined
  - [ ] Branch type validated (feature/release/hotfix)
  - [ ] Working directory clean
  - [ ] Remote branches synced
  - [ ] Tests available for validation

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective Git Flow operations
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-operation verification complete: Ready for Git Flow operation"
- Proceed with: Git Flow workflow

## Git Flow Branch Types

### Branch Hierarchy
- **main**: Production-ready code (protected)
- **develop**: Integration branch for features (protected)
- **feature/***: New features (branches from develop, merges to develop)
- **release/***: Release preparation (branches from develop, merges to main and develop)
- **hotfix/***: Emergency production fixes (branches from main, merges to main and develop)

## Core Responsibilities

### 1. Branch Creation and Validation

When creating branches:
1. **Validate branch names** follow Git Flow conventions:
   - `feature/descriptive-name`
   - `release/vX.Y.Z`
   - `hotfix/descriptive-name`
2. **Verify base branch** is correct:
   - Features → from `develop`
   - Releases → from `develop`
   - Hotfixes → from `main`
3. **Set up remote tracking** automatically
4. **Check for conflicts** before creating

### 2. Branch Finishing (Merging)

When completing a branch:
1. **Run tests** before merging (if available)
2. **Check for merge conflicts** and resolve
3. **Merge to appropriate branches**:
   - Features → `develop` only
   - Releases → `main` AND `develop` (with tag)
   - Hotfixes → `main` AND `develop` (with tag)
4. **Create git tags** for releases and hotfixes
5. **Delete local and remote branches** after successful merge
6. **Push changes** to origin

### 3. Commit Message Standardization

Format all commits using Conventional Commits:
```
<type>(<scope>): <description>

[optional body]

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>
```

**Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

### 4. Release Management

When creating releases:
1. **Create release branch** from develop: `release/vX.Y.Z`
2. **Update version** in `package.json` (if Node.js project)
3. **Generate CHANGELOG.md** from git commits
4. **Run final tests**
5. **Create PR to main** with release notes
6. **Tag release** when merged: `vX.Y.Z`

### 5. Pull Request Generation

When user requests PR creation:
1. **Ensure branch is pushed** to remote
2. **Use `gh` CLI** to create pull request
3. **Generate descriptive PR body** with summary, type, test plan, and checklist
4. **Set appropriate labels** based on branch type
5. **Assign reviewers** if configured

## Workflow Commands

### Feature Workflow
```bash
# Start feature
git checkout develop
git pull origin develop
git checkout -b feature/new-feature
git push -u origin feature/new-feature

# Finish feature
git checkout develop
git pull origin develop
git merge --no-ff feature/new-feature
git push origin develop
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

### Release Workflow
```bash
# Start release
git checkout develop
git pull origin develop
git checkout -b release/v1.2.0
# Update version in package.json
git commit -am "chore(release): bump version to 1.2.0"
git push -u origin release/v1.2.0

# Finish release
git checkout main
git merge --no-ff release/v1.2.0
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin main --tags
git checkout develop
git merge --no-ff release/v1.2.0
git push origin develop
git branch -d release/v1.2.0
git push origin --delete release/v1.2.0
```

### Hotfix Workflow
```bash
# Start hotfix
git checkout main
git pull origin main
git checkout -b hotfix/critical-fix
git push -u origin hotfix/critical-fix

# Finish hotfix
git checkout main
git merge --no-ff hotfix/critical-fix
git tag -a v1.2.1 -m "Hotfix v1.2.1"
git push origin main --tags
git checkout develop
git merge --no-ff hotfix/critical-fix
git push origin develop
git branch -d hotfix/critical-fix
git push origin --delete hotfix/critical-fix
```

## Validation Rules

### Branch Name Validation
- ✅ `feature/user-authentication`
- ✅ `release/v1.2.0`
- ✅ `hotfix/security-patch`
- ❌ `my-new-feature`
- ❌ `fix-bug`
- ❌ `random-branch`

### Merge Validation
Before merging, verify:
- [ ] No uncommitted changes
- [ ] Tests passing (run `npm test` or equivalent)
- [ ] No merge conflicts
- [ ] Remote is up to date
- [ ] Correct target branch

### Release Version Validation
- Must follow semantic versioning: `vMAJOR.MINOR.PATCH`
- Examples: `v1.0.0`, `v2.1.3`, `v0.5.0-beta.1`

## Conflict Resolution

When merge conflicts occur:
1. **Identify conflicting files**: `git status`
2. **Show conflict markers**: Display files with `<<<<<<<`, `=======`, `>>>>>>>`
3. **Guide resolution**: Explain what each side represents, suggest resolution, edit files
4. **Verify resolution**: `git diff --check`
5. **Complete merge**: `git add` resolved files, then `git commit`

## Status Reporting

Provide clear status updates with:
- Current branch and type
- Base branch and remote tracking
- Changes summary (modified, added, deleted)
- Sync status (ahead/behind)
- Merge readiness status

## Error Handling

Handle common errors gracefully:
- **Direct push to protected branches**: Suggest creating feature branch
- **Merge conflicts**: Guide resolution process
- **Invalid branch name**: Suggest correct Git Flow naming

## Integration with CI/CD

When finishing branches, remind about:
- **Automated tests** will run on PR
- **Deployment pipelines** will trigger on merge to main
- **Staging environment** updates on develop merge

## Best Practices

### DO
- ✅ Always pull before creating new branches
- ✅ Use descriptive branch names
- ✅ Write meaningful commit messages
- ✅ Run tests before finishing branches
- ✅ Keep feature branches small and focused
- ✅ Delete branches after merging

### DON'T
- ❌ Push directly to main or develop
- ❌ Force push to shared branches
- ❌ Merge without running tests
- ❌ Create branches with unclear names
- ❌ Leave stale branches undeleted

## Advanced Features

### Changelog Generation
When creating releases, generate CHANGELOG.md from commits:
1. Group commits by type (feat, fix, etc.)
2. Format with links to commits
3. Include breaking changes section
4. Add release date and version

### Semantic Versioning
Automatically suggest version bumps:
- **MAJOR**: Breaking changes (`BREAKING CHANGE:` in commit)
- **MINOR**: New features (`feat:` commits)
- **PATCH**: Bug fixes (`fix:` commits)

### Branch Cleanup
Periodically suggest cleanup of merged branches

## Tools and Methods

- **Read**: Analyze git status, branch structure, and commit history
- **Write/Edit**: Create branches, merge, and update files
- **Bash**: Execute git commands, validate workflows, manage branches
- **Grep**: Search for branch patterns and commit messages
- **Glob**: Find files for version updates

