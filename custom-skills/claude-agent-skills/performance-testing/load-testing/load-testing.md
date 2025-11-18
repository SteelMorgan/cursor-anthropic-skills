---
name: load-testing
description: Load testing and stress testing specialist. Use PROACTIVELY for creating comprehensive load test scenarios, analyzing performance under stress, and identifying system bottlenecks and capacity limits.
enforcement_level: HIGH
violation_consequence: Applications may fail under load, have unknown capacity limits, or experience performance degradation, leading to poor user experience and system failures
---

# Load Testing

This skill provides comprehensive guidance for creating load test scenarios, analyzing performance under stress, and identifying system bottlenecks and capacity limits.

## Overview

Load testing involves creating realistic test scenarios, executing progressive load tests, and analyzing system performance under various load conditions. This skill provides systematic approaches to load testing as a load testing specialist focused on performance testing and capacity planning.

## ✓ Pre-Testing Checklist

**BEFORE starting load testing, verify:**

```yaml
Checklist:
  - [ ] Performance requirements and SLAs defined
  - [ ] Test environment configured
  - [ ] Load testing tools selected
  - [ ] User scenarios and load patterns created
  - [ ] Monitoring and metrics collection setup
  - [ ] Baseline performance established

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective load testing
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-testing verification complete: Ready for load testing"
- Proceed with: Load testing workflow

## Focus Areas

- **Load testing strategy** design and execution
- **Stress testing** and breaking point identification
- **Capacity planning** and scalability analysis
- **Performance monitoring** and bottleneck detection
- **Test scenario creation** and realistic data generation
- **Performance regression testing** and CI integration

## Approach

1. Define performance requirements and SLAs
2. Create realistic user scenarios and load patterns
3. Execute progressive load testing (baseline → target → stress)
4. Monitor system resources during testing
5. Analyze results and identify bottlenecks
6. Provide actionable optimization recommendations

## Output Deliverables

- Comprehensive load testing scripts and scenarios
- Performance baseline and target metrics
- Stress testing reports with breaking points
- System capacity recommendations
- Bottleneck analysis with optimization priorities
- CI/CD integration for performance regression testing

## Best Practices

- Focus on realistic user behavior patterns
- Provide specific recommendations for infrastructure scaling
- Include optimization priorities
- Set up continuous performance monitoring
- Integrate into CI/CD pipeline

## Tools and Methods

- **Read**: Analyze application architecture, APIs, and performance requirements
- **Write/Edit**: Create load test scripts, scenarios, and reports
- **Bash**: Execute load tests, monitor systems, and analyze results

