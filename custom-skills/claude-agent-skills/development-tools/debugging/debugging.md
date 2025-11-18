---
name: debugging
description: Debugging specialist for errors, test failures, and unexpected behavior. Use PROACTIVELY when encountering issues, analyzing stack traces, or investigating system problems.
enforcement_level: HIGH
violation_consequence: Bugs may remain unresolved, root causes may be missed, or fixes may be incomplete
---

# Debugging

This skill provides comprehensive guidance for root cause analysis and systematic debugging approaches.

## Overview

Debugging involves analyzing errors, identifying root causes, and implementing fixes. This skill provides systematic approaches to debugging as an expert debugger specializing in root cause analysis.

## ✓ Pre-Debugging Checklist

**BEFORE starting debugging, verify:**

```yaml
Checklist:
  - [ ] Error message and stack trace captured
  - [ ] Reproduction steps identified
  - [ ] Error context understood
  - [ ] Recent code changes reviewed
  - [ ] Logs and error messages accessible

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective debugging
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-debugging verification complete: Ready to debug"
- Proceed with: Debugging workflow

## Debugging Process

When invoked:
1. Capture error message and stack trace
2. Identify reproduction steps
3. Isolate the failure location
4. Implement minimal fix
5. Verify solution works

## Debugging Methodology

- Analyze error messages and logs
- Check recent code changes
- Form and test hypotheses
- Add strategic debug logging
- Inspect variable states

## Output Format

For each issue, provide:
- **Root cause explanation**: Clear explanation of why the error occurred
- **Evidence supporting the diagnosis**: Logs, stack traces, code patterns that support the diagnosis
- **Specific code fix**: Exact code changes needed to fix the issue
- **Testing approach**: How to verify the fix works and doesn't introduce regressions
- **Prevention recommendations**: How to prevent similar issues in the future

## Tools and Methods

- **Read**: Analyze code files, logs, and error messages
- **Write/Edit**: Implement fixes and add debug logging
- **Bash**: Run commands to reproduce issues, check logs
- **Grep**: Search for error patterns, related code, recent changes

## Best Practices

- Focus on fixing the underlying issue, not just symptoms
- Use systematic approach: reproduce → isolate → fix → verify
- Add strategic logging to understand execution flow
- Test hypotheses methodically
- Document findings for future reference
