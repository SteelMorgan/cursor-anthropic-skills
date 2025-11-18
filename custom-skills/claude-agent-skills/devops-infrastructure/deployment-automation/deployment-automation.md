---
name: deployment-automation
description: This skill provides expertise in CI/CD and deployment automation. This skill should be used for pipeline configuration, Docker containers, Kubernetes deployments, GitHub Actions, or infrastructure automation workflows. Focuses on production-ready configs.
enforcement_level: HIGH
violation_consequence: Deployments may fail, lack proper rollback procedures, or introduce security vulnerabilities
---

# Deployment Automation

This skill provides comprehensive guidance for automated deployments and container orchestration. It emphasizes production-ready configurations with proper security and rollback procedures.

## Overview

Deployment automation involves creating CI/CD pipelines, containerizing applications, and automating infrastructure deployments. This skill provides systematic approaches to deployment automation and container orchestration.

## ✓ Pre-Deployment Checklist

**BEFORE setting up deployment automation, verify:**

```yaml
Checklist:
  - [ ] Application build process defined
  - [ ] Containerization strategy selected
  - [ ] Deployment target identified (K8s/Docker/etc)
  - [ ] Environment configurations prepared
  - [ ] Rollback procedures planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective deployment automation
- Next step: Gather missing requirements before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-deployment verification complete: Ready to automate"
- Proceed with: Deployment automation workflow

## Focus Areas

### CI/CD Pipelines

- GitHub Actions, GitLab CI, Jenkins
- Build automation
- Test integration
- Artifact management

### Docker Containerization

- Multi-stage builds
- Security best practices
- Image optimization
- Container registries

### Kubernetes Deployments

- Deployment manifests
- Service configuration
- ConfigMaps and Secrets
- Health checks

### Infrastructure as Code

- Terraform, CloudFormation
- Environment management
- State management
- Module reuse

### Monitoring and Logging

- Application monitoring
- Log aggregation
- Alerting setup
- Performance metrics

### Zero-Downtime Deployment

- Blue-green deployments
- Canary deployments
- Rolling updates
- Rollback procedures

## Approach

1. **Automate everything**: No manual deployment steps
2. **Build once, deploy anywhere**: Environment configs
3. **Fast feedback loops**: Fail early in pipelines
4. **Immutable infrastructure**: Principles
5. **Comprehensive health checks**: And rollback plans

## Output Format

Provide:
- Complete CI/CD pipeline configuration
- Dockerfile with security best practices
- Kubernetes manifests or docker-compose files
- Environment configuration strategy
- Monitoring/alerting setup basics
- Deployment runbook with rollback procedures

## Best Practices

- Focus on production-ready configs
- Include comments explaining critical decisions
- Implement proper security measures
- Ensure rollback capabilities
- Monitor deployments continuously
- Document all procedures

Focus on production-ready configs. Include comments explaining critical decisions.

