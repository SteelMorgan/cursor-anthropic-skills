---
name: mlops
description: This skill provides expertise in ML infrastructure and operations. This skill should be used for ML pipelines, experiment tracking, model registries, automated retraining, data versioning, or MLOps platform implementation. Always specify cloud provider.
enforcement_level: HIGH
violation_consequence: ML infrastructure may fail, experiments may be lost, or models may lack proper versioning, leading to reproducibility issues
---

# MLOps

This skill provides comprehensive guidance for ML infrastructure and automation across cloud platforms. It emphasizes cloud-native solutions and operational excellence.

## Overview

MLOps involves orchestrating ML pipelines, tracking experiments, managing model registries, and automating ML workflows. This skill provides systematic approaches to ML infrastructure management.

## Focus Areas

### ML Pipeline Orchestration

- Kubeflow, Airflow, cloud-native pipelines
- Pipeline design and error handling
- Dependency management
- Retry strategies

### Experiment Tracking

- MLflow, W&B, Neptune, Comet
- Experiment organization
- Metric tracking
- Artifact management

### Model Registry and Versioning

- Model versioning strategies
- Model registry setup
- Model metadata management
- Model lifecycle management

### Data Versioning

- DVC, Delta Lake, Feature Store
- Data lineage tracking
- Data quality monitoring
- Data governance

### Automated Model Retraining

- Retraining triggers
- Automated pipelines
- Model evaluation
- Deployment automation

### Multi-Cloud ML Infrastructure

- Cloud provider selection
- Cross-cloud patterns
- Vendor lock-in mitigation
- Cost optimization

## Cloud-Specific Expertise

### AWS

- SageMaker pipelines and experiments
- SageMaker Model Registry and endpoints
- AWS Batch for distributed training
- S3 for data versioning
- CloudWatch for model monitoring

### Azure

- Azure ML pipelines and designer
- Azure ML Model Registry
- Azure ML compute clusters
- Azure Data Lake for ML data
- Application Insights for ML monitoring

### GCP

- Vertex AI pipelines and experiments
- Vertex AI Model Registry
- Vertex AI training and prediction
- Cloud Storage with versioning
- Cloud Monitoring for ML metrics

## Approach

1. Choose cloud-native when possible, open-source for portability
2. Implement feature stores for consistency
3. Use managed services to reduce operational overhead
4. Design for multi-region model serving
5. Cost optimization through spot instances and autoscaling

## Output Format

Provide:
- ML pipeline code for chosen platform
- Experiment tracking setup with cloud integration
- Model registry configuration and CI/CD
- Feature store implementation
- Data versioning and lineage tracking
- Cost analysis and optimization recommendations
- Disaster recovery plan for ML systems
- Model governance and compliance setup

## Best Practices

- Always specify cloud provider
- Include Terraform/IaC for infrastructure setup
- Monitor ML systems continuously
- Plan for disaster recovery
- Document all procedures

Always specify cloud provider. Include Terraform/IaC for infrastructure setup.

