---
name: network-engineering
description: This skill provides expertise in network connectivity and infrastructure. This skill should be used for debugging network issues, load balancer configuration, DNS resolution, SSL/TLS setup, CDN optimization, or traffic analysis. Includes tcpdump/wireshark commands when relevant.
enforcement_level: HIGH
violation_consequence: Network issues may remain unresolved, connectivity problems may persist, or security vulnerabilities may be introduced
---

# Network Engineering

This skill provides comprehensive guidance for application networking and troubleshooting. It emphasizes systematic network analysis and security.

## Overview

Network engineering involves configuring network infrastructure, troubleshooting connectivity issues, and optimizing network performance. This skill provides systematic approaches to network configuration and debugging.

## ✓ Pre-Network Checklist

**BEFORE configuring network, verify:**

```yaml
Checklist:
  - [ ] Network requirements defined
  - [ ] Connectivity issues identified
  - [ ] Security requirements specified
  - [ ] Performance targets established
  - [ ] DNS and SSL requirements known

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective network configuration
- Next step: Gather missing requirements before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-network verification complete: Ready to configure"
- Proceed with: Network configuration workflow

## Focus Areas

### DNS Configuration and Debugging

- DNS resolution chain
- DNS records configuration
- DNS troubleshooting
- DNS security (DNSSEC)

### Load Balancer Setup

- nginx, HAProxy, ALB configuration
- Health checks
- SSL termination
- Traffic distribution

### SSL/TLS Setup

- Certificate management
- Certificate chain validation
- HTTPS enforcement
- TLS version configuration

### Network Performance

- Latency analysis
- Bandwidth optimization
- Connection pooling
- Traffic patterns

### CDN Configuration

- Cache strategies
- Edge location optimization
- Cache invalidation
- Performance monitoring

### Firewall Rules

- Security groups
- Network ACLs
- Firewall policies
- Access control

## Approach

1. **Test connectivity** at each layer (ping, telnet, curl)
2. **Check DNS resolution** chain completely
3. **Verify SSL certificates** and chain of trust
4. **Analyze traffic patterns** and bottlenecks
5. **Document network topology** clearly

## Output Format

Provide:
- Network diagnostic commands and results
- Load balancer configuration files
- SSL/TLS setup with certificate chains
- Traffic flow diagrams (mermaid/ASCII)
- Firewall rules with security rationale
- Performance metrics and optimization steps

## Best Practices

- Include tcpdump/wireshark commands when relevant
- Test from multiple vantage points
- Document network topology
- Verify security configurations
- Monitor network performance continuously

Include tcpdump/wireshark commands when relevant. Test from multiple vantage points.

