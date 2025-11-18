---
name: neon-database-architecture
description: Neon database architecture specialist. Use PROACTIVELY for database schema design, Drizzle ORM integration, query optimization, and serverless performance tuning. Expert in connection management and database migrations.
enforcement_level: HIGH
violation_consequence: Database schema may be inefficient, queries may be slow, or serverless performance may be poor
---

# Neon Database Architecture

This skill provides comprehensive guidance for schema design, ORM integration, and serverless performance optimization with Neon database.

## Overview

Neon database architecture involves designing schemas, integrating with Drizzle ORM, optimizing queries, and managing connections in serverless environments. This skill provides systematic approaches to Neon database design.

## Work Process

### 1. Environment Analysis
- Find Drizzle configuration files
- Check database connection setup
- Identify schema definitions

### 2. Implementation Focus
- Use Drizzle ORM with `neon-http` adapter
- Optimize for serverless cold starts
- Implement efficient connection patterns
- Design scalable schema structures

## Technical Standards

### Connection Management
- Use environment variables for DATABASE_URL
- Implement proper lifecycle in serverless functions
- Handle connection errors with retry logic

### Schema Design
- Design normalized, efficient schemas
- Use appropriate Postgres types (JSONB, arrays, enums)
- Implement proper constraints and indexes

### Query Optimization
- Use prepared statements for repeated queries
- Implement batch operations efficiently
- Optimize for Neon's serverless characteristics

## Neon Serverless Guidelines

### Installation
```bash
npm install @neondatabase/serverless drizzle-orm
npm install -D drizzle-kit
```

### Connection Setup
- Use `drizzle` with `neon-http` adapter
- Create SQL client with `neon()` function
- Export database instance

### Schema Design
- Use Drizzle schema definitions
- Leverage Postgres-specific types
- Implement proper relationships

### Query Optimization
- Efficient batch operations
- Prepared statements for repeated queries
- Transaction handling

### Error Handling
- Connection timeout handling
- Safe query wrappers
- Error recovery strategies

## Best Practices

Always provide working code examples with clear explanations and verification steps. Focus on serverless optimization and efficient connection management.

