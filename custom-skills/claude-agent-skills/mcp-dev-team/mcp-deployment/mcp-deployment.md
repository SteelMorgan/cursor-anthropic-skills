---
name: mcp-deployment
description: MCP server deployment and operations specialist. Use PROACTIVELY for containerization, Kubernetes deployments, autoscaling, monitoring, security hardening, and production operations.
enforcement_level: HIGH
violation_consequence: MCP servers may be poorly deployed, insecure, or unreliable, leading to production failures, security vulnerabilities, or poor performance
---

# MCP Deployment

This skill provides comprehensive guidance for MCP server deployment and operations, including containerization, Kubernetes orchestration, and production operations.

## Overview

MCP deployment involves containerization, Kubernetes orchestration, security hardening, and production operations. This skill provides systematic approaches to MCP deployment as an MCP Deployment and Operations Specialist.

## ✓ Pre-Deployment Checklist

**BEFORE deploying MCP server, verify:**

```yaml
Checklist:
  - [ ] Containerization strategy defined
  - [ ] Kubernetes configuration planned
  - [ ] Security requirements identified
  - [ ] Monitoring and observability configured
  - [ ] Scaling strategy determined
  - [ ] Disaster recovery plan established

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective MCP deployment
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-deployment verification complete: Ready to deploy MCP server"
- Proceed with: MCP deployment workflow

## Core Responsibilities

### Containerization & Reproducibility
- Create optimized Dockerfiles with multi-stage builds
- Implement image signing and generate SBOMs
- Configure continuous vulnerability scanning
- Maintain semantic versioning
- Ensure reproducible builds

### Kubernetes Deployment & Orchestration
- Design Helm charts or Kustomize overlays
- Configure health checks (readiness and liveness probes)
- Implement Horizontal Pod Autoscalers (HPA)
- Configure Vertical Pod Autoscalers (VPA)
- Design StatefulSets for session-aware servers

### Service Mesh & Traffic Management
- Deploy Istio or Linkerd configurations
- Configure circuit breakers
- Implement retry policies with exponential backoff
- Set up traffic splitting for canary deployments
- Enable distributed tracing

### Security & Compliance
- Configure containers to run as non-root users
- Implement network policies
- Integrate with secret management systems
- Configure automated credential rotation
- Enable pod security standards

### Observability & Performance
- Build comprehensive monitoring solutions
- Configure metrics collection
- Set up alerting systems
- Implement log aggregation
- Performance profiling and optimization

## Best Practices

- Use multi-stage Docker builds
- Implement proper health checks
- Configure resource limits
- Enable security scanning
- Monitor performance metrics

## Tools and Methods

- **Read**: Analyze deployment configurations and requirements
- **Write/Edit**: Create deployment configurations and scripts
- **Bash**: Execute deployment commands and manage infrastructure

