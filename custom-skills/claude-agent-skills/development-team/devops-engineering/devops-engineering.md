---
name: devops-engineering
description: DevOps and infrastructure specialist for CI/CD, deployment automation, and cloud operations. Use PROACTIVELY for pipeline setup, infrastructure provisioning, monitoring, security implementation, and deployment optimization.
enforcement_level: HIGH
violation_consequence: CI/CD pipelines may fail, infrastructure may be insecure, or deployments may be unreliable
---

# DevOps Engineering

This skill provides comprehensive guidance for infrastructure automation, CI/CD pipelines, and cloud-native deployments. It emphasizes Infrastructure as Code and progressive deployment strategies.

## Overview

DevOps engineering involves automating infrastructure provisioning, creating CI/CD pipelines, implementing monitoring, and ensuring security. This skill provides systematic approaches to DevOps practices.

## Core DevOps Framework

### Infrastructure as Code
- Terraform/CloudFormation: Infrastructure provisioning and state management
- Ansible/Chef/Puppet: Configuration management and deployment automation
- Docker/Kubernetes: Containerization and orchestration strategies
- Helm Charts: Kubernetes application packaging and deployment
- Cloud Platforms: AWS, GCP, Azure service integration and optimization

### CI/CD Pipeline Architecture
- Build Systems: Jenkins, GitHub Actions, GitLab CI, Azure DevOps
- Testing Integration: Unit, integration, security, and performance testing
- Artifact Management: Container registries, package repositories
- Deployment Strategies: Blue-green, canary, rolling deployments
- Environment Management: Development, staging, production consistency

## Technical Implementation

### CI/CD Pipeline Setup
- Complete pipeline configuration with testing stages
- Container image building and pushing
- Automated deployment to staging and production
- Health checks and smoke tests
- Rollback procedures

### Infrastructure as Code
- Terraform configurations for cloud resources
- VPC and networking setup
- Kubernetes cluster provisioning
- Database and cache infrastructure
- Load balancer configuration

### Kubernetes Deployment
- Helm charts for application deployment
- Horizontal Pod Autoscaler configuration
- Resource limits and requests
- Health probes and readiness checks
- Service and ingress configuration

### Monitoring and Observability
- Prometheus metrics collection
- Grafana dashboards
- Alerting rules and notification channels
- Application performance monitoring
- Log aggregation and analysis

### Security and Compliance
- Container image vulnerability scanning
- Kubernetes security benchmarks
- Network policy validation
- Secret scanning in codebase
- Infrastructure security scanning

## Deployment Strategies

### Blue-Green Deployment
- Deploy new version to green environment
- Health check validation
- Traffic switching
- Old version cleanup

### Canary Deployment
- Gradual traffic shifting
- Monitoring and rollback capabilities
- Service mesh integration

## Best Practices

DevOps implementations should prioritize:
1. **Infrastructure as Code** - Everything versioned and reproducible
2. **Automated Testing** - Security, performance, and functional validation
3. **Progressive Deployment** - Risk mitigation through staged rollouts
4. **Comprehensive Monitoring** - Observability across all system layers
5. **Security by Design** - Built-in security controls and compliance checks

Always include rollback procedures, disaster recovery plans, and comprehensive documentation for all automation workflows.
