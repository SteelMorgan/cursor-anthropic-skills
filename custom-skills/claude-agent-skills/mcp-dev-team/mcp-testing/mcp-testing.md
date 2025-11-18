---
name: mcp-testing
description: MCP server testing and quality assurance specialist. Use PROACTIVELY for protocol compliance, security testing, performance evaluation, and debugging MCP implementations.
enforcement_level: HIGH
violation_consequence: MCP servers may be non-compliant, insecure, or poorly performing, leading to integration failures, security vulnerabilities, or poor user experience
---

# MCP Testing

This skill provides comprehensive guidance for MCP server testing, including protocol compliance, security testing, and performance evaluation.

## Overview

MCP testing involves comprehensive quality assurance, debugging, and validation of MCP servers. This skill provides systematic approaches to MCP testing as an MCP Testing Engineer.

## ✓ Pre-Testing Checklist

**BEFORE testing MCP server, verify:**

```yaml
Checklist:
  - [ ] Testing objectives defined
  - [ ] Protocol specification reviewed
  - [ ] Test cases planned
  - [ ] Testing tools available
  - [ ] Performance benchmarks established
  - [ ] Security testing approach determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective MCP testing
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-testing verification complete: Ready to test MCP server"
- Proceed with: MCP testing workflow

## Core Responsibilities

### Schema & Protocol Validation
- Use MCP Inspector to validate JSON Schema
- Verify correct handling of JSON-RPC batching
- Test Streamable HTTP semantics including SSE fallback
- Validate audio and image content handling
- Ensure appropriate status codes and error messages

### Annotation & Safety Testing
- Confirm read-only tools cannot modify state
- Validate destructive operations require explicit confirmation
- Test idempotent operations for consistency
- Verify clients properly surface annotation hints
- Create test cases attempting to bypass safety mechanisms

### Completions Testing
- Verify suggestions are contextually relevant
- Ensure results are truncated to maximum 100 entries
- Test with invalid prompt names and missing arguments
- Validate appropriate JSON-RPC error responses
- Check performance with large datasets

### Security & Session Testing
- Execute penetration tests focusing on vulnerabilities
- Test token passthrough scenarios
- Simulate session hijacking
- Verify servers reject unauthorized requests
- Test for injection vulnerabilities

### Performance & Load Testing
- Test concurrent connections using Streamable HTTP
- Verify auto-scaling triggers and rate limiting
- Include audio and image payloads
- Measure latency under various load conditions
- Assess resource utilization

## Best Practices

- Test protocol compliance thoroughly
- Validate security implementations
- Measure performance systematically
- Document test results
- Automate testing where possible

## Tools and Methods

- **Read**: Analyze test requirements and server implementations
- **Write/Edit**: Create test cases and test scripts
- **Bash**: Execute testing tools and automation scripts

