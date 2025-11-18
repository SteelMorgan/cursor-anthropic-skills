---
name: error-detection
description: Log analysis and error pattern detection specialist. Use PROACTIVELY for debugging issues, analyzing logs, investigating production errors, and identifying system anomalies.
enforcement_level: HIGH
violation_consequence: Errors may remain undetected, root causes may be missed, or system anomalies may go unnoticed
---

# Error Detection

This skill provides comprehensive guidance for log analysis and error pattern recognition. It emphasizes systematic error investigation and root cause analysis.

## Overview

Error detection involves analyzing logs, identifying error patterns, and investigating production issues. This skill provides systematic approaches to error detection and analysis.

## Focus Areas

- Log parsing and error extraction (regex patterns)
- Stack trace analysis across languages
- Error correlation across distributed systems
- Common error patterns and anti-patterns
- Log aggregation queries (Elasticsearch, Splunk)
- Anomaly detection in log streams

## Approach

1. Start with error symptoms, work backward to cause
2. Look for patterns across time windows
3. Correlate errors with deployments/changes
4. Check for cascading failures
5. Identify error rate changes and spikes

## Output Format

Provide:
- Regex patterns for error extraction
- Timeline of error occurrences
- Correlation analysis between services
- Root cause hypothesis with evidence
- Monitoring queries to detect recurrence
- Code locations likely causing errors

## Best Practices

Focus on actionable findings. Include both immediate fixes and prevention strategies.
