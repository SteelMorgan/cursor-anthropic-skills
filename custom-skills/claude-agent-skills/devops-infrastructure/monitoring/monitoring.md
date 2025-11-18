---
name: monitoring
description: This skill provides expertise in monitoring and observability infrastructure. This skill should be used for metrics collection, alerting systems, log aggregation, distributed tracing, SLA monitoring, or performance dashboards. Focuses on actionable alerts only.
enforcement_level: HIGH
violation_consequence: System issues may go undetected, incidents may escalate, or performance problems may remain unresolved
---

# Monitoring

This skill provides comprehensive guidance for observability infrastructure and performance analytics. It emphasizes actionable monitoring with minimal alert fatigue.

## Overview

Monitoring involves collecting metrics, aggregating logs, tracing distributed systems, and creating dashboards for observability. This skill provides systematic approaches to monitoring setup and optimization.

## ✓ Pre-Monitoring Checklist

**BEFORE setting up monitoring, verify:**

```yaml
Checklist:
  - [ ] Monitoring requirements defined
  - [ ] Metrics to track identified
  - [ ] Alert thresholds determined
  - [ ] Log aggregation strategy planned
  - [ ] Dashboard requirements specified

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective monitoring setup
- Next step: Gather missing requirements before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-monitoring verification complete: Ready to setup"
- Proceed with: Monitoring setup workflow

## Focus Areas

### Metrics Collection

- Prometheus, InfluxDB, DataDog
- Custom metrics
- Business metrics
- Infrastructure metrics

### Log Aggregation

- ELK stack, Fluentd, Loki
- Log parsing and analysis
- Log retention policies
- Cost optimization

### Distributed Tracing

- Jaeger, Zipkin, OpenTelemetry
- Trace correlation
- Performance analysis
- Error tracking

### Alerting Systems

- Alert configuration
- Notification channels
- Alert grouping
- Alert fatigue reduction

### Dashboard Creation

- Grafana dashboards
- Custom visualizations
- Real-time monitoring
- Historical analysis

### SLA/SLO Monitoring

- Service level objectives
- Error budgets
- Incident response
- Reporting automation

## Approach

1. **Four Golden Signals**: Latency, traffic, errors, saturation
2. **RED method**: Rate, Errors, Duration
3. **USE method**: Utilization, Saturation, Errors
4. **Alert on symptoms**, not causes
5. **Minimize alert fatigue** with smart grouping

## Output Format

Provide:
- Complete monitoring stack configuration
- Prometheus rules and Grafana dashboards
- Log parsing and alerting rules
- OpenTelemetry instrumentation setup
- SLA monitoring and reporting automation
- Runbooks for common alert scenarios

## Best Practices

- Include retention policies and cost optimization strategies
- Focus on actionable alerts only
- Monitor symptoms, not causes
- Reduce alert fatigue
- Provide clear runbooks

Include retention policies and cost optimization strategies. Focus on actionable alerts only.

