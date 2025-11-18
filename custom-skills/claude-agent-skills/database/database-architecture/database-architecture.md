---
name: database-architecture
description: Database architecture and design specialist. Use PROACTIVELY for database design decisions, data modeling, scalability planning, microservices data patterns, and database technology selection.
enforcement_level: HIGH
violation_consequence: Database design may be inefficient, scalability may be limited, or architecture may not support business requirements
---

# Database Architecture

This skill provides comprehensive guidance for database design, data modeling, and scalable database architectures. It emphasizes domain-driven design and performance by design.

## Overview

Database architecture involves designing database structures, selecting technologies, planning scalability, and implementing patterns for microservices. This skill provides systematic approaches to database architecture.

## Core Architecture Framework

### Database Design Philosophy

- **Domain-Driven Design**: Align database structure with business domains
- **Data Modeling**: Entity-relationship design, normalization strategies, dimensional modeling
- **Scalability Planning**: Horizontal vs vertical scaling, sharding strategies
- **Technology Selection**: SQL vs NoSQL, polyglot persistence, CQRS patterns
- **Performance by Design**: Query patterns, access patterns, data locality

### Architecture Patterns

- **Single Database**: Monolithic applications with centralized data
- **Database per Service**: Microservices with bounded contexts
- **Shared Database Anti-pattern**: Legacy system integration challenges
- **Event Sourcing**: Immutable event logs with projections
- **CQRS**: Command Query Responsibility Segregation

## Technical Implementation

### Data Modeling Framework

- Entity-relationship design with proper constraints
- Business rules embedded in schema
- Normalization strategies
- Versioning support
- State machine patterns

### Microservices Data Architecture

- Event-driven microservices architecture
- Domain boundary separation
- Event sourcing patterns
- Saga patterns for distributed transactions
- Event publishing and consumption

### Polyglot Persistence Strategy

- Relational DB for transactional data
- Document DB for flexible schemas
- Key-value store for caching
- Search engine for full-text search
- Time-series DB for analytics

### Database Migration Strategy

- Migration framework with rollback support
- Checkpoint creation
- Atomic migration execution
- Failure handling and recovery

## Scalability Architecture Patterns

### Read Replica Configuration

- Master database configuration
- Replication user setup
- Read replica configuration
- WAL archiving

### Horizontal Sharding Strategy

- Application-level sharding
- Consistent hashing
- Customer data distribution
- Cross-shard analytics

## Architecture Decision Framework

### Database Technology Selection Matrix

- Relational databases for ACID transactions
- Document databases for flexible schema
- Key-value stores for caching
- Search engines for full-text search
- Time-series databases for metrics

## Performance and Monitoring

### Database Health Monitoring

- Connection monitoring
- Lock monitoring
- Query performance analysis
- Index usage analysis

## Best Practices

Architecture decisions should prioritize:
1. **Business Domain Alignment** - Database boundaries should match business boundaries
2. **Scalability Path** - Plan for growth from day one, but start simple
3. **Data Consistency Requirements** - Choose consistency models based on business requirements
4. **Operational Simplicity** - Prefer managed services and standard patterns
5. **Cost Optimization** - Right-size databases and use appropriate storage tiers

Always provide concrete architecture diagrams, data flow documentation, and migration strategies for complex database designs.
