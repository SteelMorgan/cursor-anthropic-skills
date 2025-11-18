---
name: performance-engineering
description: Profile applications, optimize bottlenecks, and implement caching strategies. Handles load testing, CDN setup, and query optimization. Use PROACTIVELY for performance issues or optimization tasks.
enforcement_level: HIGH
violation_consequence: Applications may have poor performance, unoptimized bottlenecks, or inefficient caching, leading to slow response times and poor user experience
---

# Performance Engineering

This skill provides comprehensive guidance for application profiling, optimization, caching strategies, and performance monitoring.

## Overview

Performance engineering involves profiling applications, optimizing bottlenecks, implementing caching strategies, and setting up performance monitoring. This skill provides systematic approaches to performance engineering as a performance engineer specializing in application optimization and scalability.

## ✓ Pre-Engineering Checklist

**BEFORE starting performance engineering, verify:**

```yaml
Checklist:
  - [ ] Current performance metrics measured
  - [ ] Performance bottlenecks identified
  - [ ] Caching strategy planned
  - [ ] Load testing approach determined
  - [ ] Performance budgets established
  - [ ] Monitoring setup planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective performance engineering
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-engineering verification complete: Ready for performance engineering"
- Proceed with: Performance engineering workflow

## Focus Areas

- **Application profiling** (CPU, memory, I/O)
- **Load testing** with JMeter/k6/Locust
- **Caching strategies** (Redis, CDN, browser)
- **Database query** optimization
- **Frontend performance** (Core Web Vitals)
- **API response time** optimization

## Approach

1. Measure before optimizing
2. Focus on biggest bottlenecks first
3. Set performance budgets
4. Cache at appropriate layers
5. Load test realistic scenarios

## Output Deliverables

- Performance profiling results with flamegraphs
- Load test scripts and results
- Caching implementation with TTL strategy
- Optimization recommendations ranked by impact
- Before/after performance metrics
- Monitoring dashboard setup

## Best Practices

- Include specific numbers and benchmarks
- Focus on user-perceived performance
- Profile before optimizing
- Set performance budgets
- Monitor continuously

## Tools and Methods

- **Read**: Analyze code, performance profiles, and metrics
- **Write/Edit**: Optimize code, implement caching, configure CDN
- **Bash**: Run profiling tools, load tests, and monitoring

