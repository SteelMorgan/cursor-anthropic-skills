---
name: cloud-migration
description: Cloud migration and infrastructure modernization specialist. Use PROACTIVELY for on-premise to cloud migrations, containerization, serverless adoption, and cloud-native transformations.
enforcement_level: HIGH
violation_consequence: Cloud migrations may fail, cause downtime, or result in cost overruns, requiring significant remediation and potential rollback
---

# Cloud Migration

This skill provides comprehensive guidance for migrating on-premise applications to cloud platforms, containerization, and adopting cloud-native architectures.

## Overview

Cloud migration involves transforming traditional applications for cloud environments through containerization, serverless adoption, and infrastructure modernization. This skill provides systematic approaches to cloud migration as a cloud migration specialist focused on transforming traditional applications.

## ✓ Pre-Migration Checklist

**BEFORE starting cloud migration, verify:**

```yaml
Checklist:
  - [ ] Current infrastructure assessed
  - [ ] Cloud platform selected (AWS/Azure/GCP)
  - [ ] Migration strategy determined (lift-and-shift, refactor, etc.)
  - [ ] Cost analysis completed
  - [ ] Security and compliance requirements understood
  - [ ] Disaster recovery plan prepared

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective cloud migration
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-migration verification complete: Ready for cloud migration"
- Proceed with: Cloud migration workflow

## Focus Areas

- **On-premise to cloud** platform migrations (AWS, Azure, GCP)
- **Containerization** with Docker and Kubernetes
- **Serverless architecture** adoption and optimization
- **Database migration** strategies and optimization
- **Network architecture** and security modernization
- **Cost optimization** and resource rightsizing

## Approach

1. **Assessment-first** migration planning
2. **Lift-and-shift** followed by optimization
3. **Gradual refactoring** to cloud-native patterns
4. **Infrastructure as Code** implementation
5. **Automated testing** and deployment pipelines
6. **Cost monitoring** and optimization cycles

## Output Deliverables

### Cloud Migration Roadmap
- Migration phases and timelines
- Resource requirements and dependencies
- Risk assessment and mitigation
- Success criteria and validation

### Containerized Configurations
- Dockerfile definitions
- Kubernetes manifests
- Container orchestration setup
- Service mesh configurations

### Infrastructure as Code
- Terraform/CloudFormation templates
- Infrastructure provisioning scripts
- Configuration management
- Environment definitions

### Migration Automation
- Data migration scripts
- Application deployment automation
- Testing automation
- Rollback procedures

### Cost Analysis
- Current cost baseline
- Cloud cost projections
- Optimization recommendations
- Cost monitoring setup

### Security and Compliance
- Security architecture design
- Compliance validation frameworks
- Identity and access management
- Network security configurations

## Migration Strategies

### Lift-and-Shift
- Move applications as-is to cloud
- Minimal code changes
- Quick migration path
- Optimize after migration

### Refactor
- Modernize for cloud-native
- Use cloud services
- Optimize architecture
- Better long-term benefits

### Hybrid Approach
- Gradual migration
- Keep some on-premise
- Cloud-native for new features
- Phased transition

## Cloud-Native Patterns

### Containerization
- Docker containerization
- Kubernetes orchestration
- Service mesh integration
- Auto-scaling configuration

### Serverless
- Function-as-a-Service adoption
- Event-driven architectures
- Serverless database patterns
- Cost optimization strategies

### Microservices
- Service decomposition
- API gateway implementation
- Service discovery
- Distributed tracing

## Best Practices

- Focus on minimizing downtime
- Maximize cloud benefits
- Include disaster recovery strategies
- Implement multi-region deployments
- Monitor costs continuously
- Optimize resource usage
- Ensure security and compliance

## Tools and Methods

- **Read**: Analyze current infrastructure, applications, and dependencies
- **Write/Edit**: Create cloud configurations, migration scripts, and IaC templates
- **Bash**: Run migration scripts, deploy infrastructure, monitor systems

## Risk Mitigation

- Comprehensive assessment before migration
- Phased migration approach
- Maintain rollback capabilities
- Test thoroughly at each phase
- Monitor system health continuously
- Document all changes and procedures

