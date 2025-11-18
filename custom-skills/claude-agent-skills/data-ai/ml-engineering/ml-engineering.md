---
name: ml-engineering
description: This skill provides expertise in ML production systems and model deployment. This skill should be used for ML pipelines, model serving, feature engineering, A/B testing, monitoring, or production ML infrastructure. Focuses on production reliability over model complexity.
enforcement_level: HIGH
violation_consequence: ML models may fail in production, perform poorly, or lack proper monitoring, leading to poor predictions or system failures
---

# ML Engineering

This skill provides comprehensive guidance for production machine learning systems, model deployment, and MLOps practices. It emphasizes production reliability and monitoring.

## Overview

ML engineering involves deploying models to production, serving predictions, monitoring model performance, and managing ML infrastructure. This skill provides systematic approaches to production ML systems.

## Focus Areas

### Model Serving

- TorchServe, TF Serving, ONNX
- API design for inference
- Scaling strategies
- Latency optimization

### Feature Engineering Pipelines

- Feature pipeline design
- Feature validation
- Feature versioning
- Feature store integration

### Model Versioning and A/B Testing

- Model versioning strategies
- A/B testing frameworks
- Gradual rollouts
- Canary deployments

### Batch and Real-time Inference

- Batch inference pipelines
- Real-time inference APIs
- Streaming inference
- Inference optimization

### Model Monitoring and Drift Detection

- Prediction quality monitoring
- Data drift detection
- Model performance tracking
- Alerting and notifications

### MLOps Best Practices

- CI/CD for ML
- Model registry
- Experiment tracking
- Reproducibility

## Approach

1. Start with simple baseline model
2. Version everything - data, features, models
3. Monitor prediction quality in production
4. Implement gradual rollouts
5. Plan for model retraining

## Output Format

Provide:
- Model serving API with proper scaling
- Feature pipeline with validation
- A/B testing framework
- Model monitoring metrics and alerts
- Inference optimization techniques
- Deployment rollback procedures

## Best Practices

- Focus on production reliability over model complexity
- Include latency requirements
- Monitor models continuously
- Plan for model retraining
- Document deployment procedures

Focus on production reliability over model complexity. Include latency requirements.

