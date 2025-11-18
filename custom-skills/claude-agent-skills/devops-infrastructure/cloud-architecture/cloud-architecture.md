---
name: cloud-architecture
description: This skill provides expertise in cloud infrastructure design and optimization for AWS/Azure/GCP. This skill should be used for infrastructure architecture, Terraform IaC, cost optimization, auto-scaling, or multi-region deployments. Prefers managed services over self-hosted.
enforcement_level: HIGH
violation_consequence: Cloud infrastructure may be inefficient, insecure, or costly, requiring significant refactoring
---

# Cloud Architecture

This skill provides comprehensive guidance for scalable, cost-effective cloud infrastructure design. It emphasizes Infrastructure as Code, cost optimization, and security best practices.

## Overview

Cloud architecture involves designing scalable, cost-effective infrastructure using cloud platforms. This skill provides systematic approaches to infrastructure design, cost optimization, and multi-region deployments.

## ✓ Pre-Architecture Checklist

**BEFORE designing cloud infrastructure, verify:**

```yaml
Checklist:
  - [ ] Application requirements and scale defined
  - [ ] Cloud platform selected (AWS/Azure/GCP)
  - [ ] Cost budget and constraints identified
  - [ ] Security requirements specified
  - [ ] Multi-region needs determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective cloud architecture design
- Next step: Gather missing requirements before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-architecture verification complete: Ready to design"
- Proceed with: Cloud architecture design workflow

## Focus Areas

### Infrastructure as Code

- Terraform, CloudFormation
- State management
- Module design
- Version control

### Multi-Cloud and Hybrid Strategies

- Multi-cloud architectures
- Hybrid cloud integration
- Vendor lock-in mitigation
- Cross-cloud patterns

### Cost Optimization and FinOps

- Right-sizing resources
- Reserved instances
- Spot instances
- Cost monitoring and alerts

### Auto-Scaling and Load Balancing

- Horizontal scaling
- Vertical scaling
- Load balancer configuration
- Scaling policies

### Serverless Architectures

- Lambda, Cloud Functions
- Event-driven patterns
- Serverless databases
- Cost optimization

### Security Best Practices

- VPC configuration
- IAM policies (least privilege)
- Encryption at rest and in transit
- Security groups and network ACLs

## Approach

1. **Cost-conscious design**: Right-size resources
2. **Automate everything**: Via IaC
3. **Design for failure**: Multi-AZ/region
4. **Security by default**: Least privilege IAM
5. **Monitor costs daily**: With alerts

## Output Format

Provide:
- Terraform modules with state management
- Architecture diagram (draw.io/mermaid format)
- Cost estimation for monthly spend
- Auto-scaling policies and metrics
- Security groups and network configuration
- Disaster recovery runbook

## Best Practices

- Prefer managed services over self-hosted
- Include cost breakdowns and savings recommendations
- Design for scalability from day one
- Implement security by default
- Monitor and optimize costs continuously

Prefer managed services over self-hosted. Include cost breakdowns and savings recommendations.

