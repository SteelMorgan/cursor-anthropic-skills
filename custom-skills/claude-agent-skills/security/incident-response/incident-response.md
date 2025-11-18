---
name: incident-response
description: This skill provides expertise in handling production incidents with urgency and precision. This skill should be used IMMEDIATELY when production issues occur. Coordinates debugging, implements fixes, and documents post-mortems.
enforcement_level: CRITICAL
violation_consequence: Production incidents may escalate, downtime may increase, or fixes may introduce new issues
---

# Incident Response

This skill provides comprehensive guidance for rapid incident response and production issue resolution. It emphasizes urgency while maintaining precision.

## ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT PROCEED WITH INCIDENT RESPONSE UNTIL YOU:**

```python
# MANDATORY first actions:
# 1. Assess severity and user impact
# 2. Stabilize the system
# 3. Gather data (logs, metrics, recent changes)
# 4. Communicate status
```

**DID YOU COMPLETE FIRST ACTIONS? Yes / No**

IF NO → STOP, complete first actions
IF YES → Output: "✅ Initial assessment complete" and continue

---

## Immediate Actions (First 5 minutes)

### 1. Assess Severity

- User impact (how many, how severe)
- Business impact (revenue, reputation)
- System scope (which services affected)

### 2. Stabilize

- Identify quick mitigation options
- Implement temporary fixes if available
- Communicate status clearly

### 3. Gather Data

- Recent deployments or changes
- Error logs and metrics
- Similar past incidents

## Investigation Protocol

### Log Analysis

- Start with error aggregation
- Identify error patterns
- Trace to root cause
- Check cascading failures

### Quick Fixes

- Rollback if recent deployment
- Increase resources if load-related
- Disable problematic features
- Implement circuit breakers

### Communication

- Brief status updates every 15 minutes
- Technical details for engineers
- Business impact for stakeholders
- ETA when reasonable to estimate

## Fix Implementation

1. Minimal viable fix first
2. Test in staging if possible
3. Roll out with monitoring
4. Prepare rollback plan
5. Document changes made

## Post-Incident

- Document timeline
- Identify root cause
- List action items
- Update runbooks
- Store in memory for future reference

## Severity Levels

- **P0**: Complete outage, immediate response
- **P1**: Major functionality broken, < 1 hour response
- **P2**: Significant issues, < 4 hour response
- **P3**: Minor issues, next business day

## Best Practices

- In incidents, speed matters but accuracy matters more
- A wrong fix can make things worse
- Communicate clearly and frequently
- Document everything for post-mortem
- Learn from each incident

Remember: In incidents, speed matters but accuracy matters more. A wrong fix can make things worse.

