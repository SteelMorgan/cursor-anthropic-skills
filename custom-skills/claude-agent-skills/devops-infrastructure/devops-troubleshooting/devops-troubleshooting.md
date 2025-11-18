---
name: devops-troubleshooting
description: This skill provides expertise in production troubleshooting and incident response. This skill should be used for debugging issues, log analysis, deployment failures, monitoring setup, or root cause analysis. Focuses on quick resolution.
enforcement_level: HIGH
violation_consequence: Production issues may remain unresolved, incidents may escalate, or root causes may be missed
---

# DevOps Troubleshooting

This skill provides comprehensive guidance for rapid incident response and debugging in production environments. It emphasizes systematic problem-solving and quick resolution.

## Overview

DevOps troubleshooting involves analyzing production issues, identifying root causes, and implementing fixes quickly. This skill provides systematic approaches to incident response and debugging.

## ✓ Pre-Troubleshooting Checklist

**BEFORE troubleshooting, verify:**

```yaml
Checklist:
  - [ ] Issue symptoms clearly defined
  - [ ] Logs and metrics accessible
  - [ ] System components identified
  - [ ] Recent changes reviewed
  - [ ] Impact assessment completed

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective troubleshooting
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-troubleshooting verification complete: Ready to troubleshoot"
- Proceed with: Troubleshooting workflow

## Focus Areas

### Log Analysis and Correlation

- ELK stack, Datadog
- Log aggregation
- Error pattern detection
- Timeline correlation

### Container Debugging

- kubectl commands
- Container logs
- Pod status checks
- Resource utilization

### Network Troubleshooting

- DNS issues
- Network connectivity
- Firewall rules
- Load balancer configuration

### Performance Bottlenecks

- Memory leaks
- CPU utilization
- Database performance
- Application bottlenecks

### Deployment Issues

- Rollback procedures
- Hotfixes
- Configuration errors
- Dependency issues

### Monitoring Setup

- Alert configuration
- Metric collection
- Dashboard creation
- Incident detection

## Approach

1. **Gather facts first**: Logs, metrics, traces
2. **Form hypothesis**: And test systematically
3. **Document findings**: For postmortem
4. **Implement fix**: With minimal disruption
5. **Add monitoring**: To prevent recurrence

## Output Format

Provide:
- Root cause analysis with evidence
- Step-by-step debugging commands
- Emergency fix implementation
- Monitoring queries to detect issue
- Runbook for future incidents
- Post-incident action items

## Best Practices

- Focus on quick resolution
- Include both temporary and permanent fixes
- Document everything for postmortem
- Implement monitoring to prevent recurrence
- Test fixes before full deployment
- Communicate clearly during incidents

Focus on quick resolution. Include both temporary and permanent fixes.

