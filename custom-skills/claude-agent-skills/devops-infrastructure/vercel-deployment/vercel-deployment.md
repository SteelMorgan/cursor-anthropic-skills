---
name: vercel-deployment
description: This skill provides expertise in Vercel platform features, edge functions, middleware, and deployment strategies. This skill should be used for Vercel deployments, performance optimization, or platform configuration. Focuses on production-ready configurations.
enforcement_level: HIGH
violation_consequence: Vercel deployments may fail, perform poorly, or lack proper monitoring, requiring significant refactoring
---

# Vercel Deployment

This skill provides comprehensive guidance for Vercel platform deployment, edge functions, serverless optimization, and performance monitoring. It emphasizes production-ready configurations.

## Overview

Vercel deployment involves configuring deployments, optimizing edge functions, managing serverless functions, and monitoring performance. This skill provides systematic approaches to Vercel platform optimization.

## ✓ Pre-Deployment Checklist

**BEFORE deploying to Vercel, verify:**

```yaml
Checklist:
  - [ ] Application build process tested
  - [ ] Environment variables configured
  - [ ] Domain and SSL setup planned
  - [ ] Performance targets defined
  - [ ] Monitoring configured

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective Vercel deployment
- Next step: Gather missing requirements before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-deployment verification complete: Ready to deploy"
- Proceed with: Vercel deployment workflow

## Core Expertise Areas

### Vercel Platform

- Deployment configuration
- Environment management
- Domain setup
- Project configuration

### Edge Functions

- Edge runtime
- Geo-distribution
- Cold start optimization
- Middleware configuration

### Serverless Functions

- API routes
- Function optimization
- Timeout management
- Error handling

### Performance Optimization

- Edge caching
- ISR (Incremental Static Regeneration)
- Image optimization
- Core Web Vitals

### CI/CD Integration

- Git workflows
- Preview deployments
- Production pipelines
- Automated testing

### Monitoring & Analytics

- Real User Monitoring
- Web Analytics
- Speed Insights
- Error tracking

### Security

- Environment variables
- Authentication
- CORS configuration
- Security headers

## Deployment Configuration

### vercel.json Configuration

- Framework detection
- Build commands
- Function configuration
- Headers and redirects
- Cron jobs

### Environment Configuration

- Production variables
- Preview variables
- Development variables
- Secret management

## Performance Optimization

### Image Optimization

- Next.js Image component
- WebP/AVIF formats
- Responsive images
- CDN caching

### ISR Configuration

- Incremental Static Regeneration
- Revalidation strategies
- Static generation
- Dynamic routes

## Best Practices

- Always provide specific deployment configurations
- Include performance optimizations
- Configure monitoring solutions
- Tailor to project scale and requirements
- Test deployments thoroughly

Always provide specific deployment configurations, performance optimizations, and monitoring solutions tailored to the project's scale and requirements.

