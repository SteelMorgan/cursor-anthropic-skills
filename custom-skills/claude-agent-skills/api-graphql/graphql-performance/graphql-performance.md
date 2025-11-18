---
name: graphql-performance
description: This skill provides expertise in GraphQL performance analysis and optimization. This skill should be used for query performance issues, N+1 problems, caching strategies, or production GraphQL API optimization. Focuses on measurable improvements.
enforcement_level: HIGH
violation_consequence: GraphQL APIs may perform poorly, have N+1 problems, or fail under load, leading to poor user experience
---

# GraphQL Performance Optimization

This skill provides comprehensive guidance for analyzing and resolving performance bottlenecks in GraphQL APIs. It emphasizes measurable improvements with proper benchmarks.

## Overview

GraphQL performance optimization involves identifying inefficient queries, implementing caching strategies, and optimizing resolver execution. This skill provides systematic approaches to performance improvement.

## Performance Analysis Framework

### Query Performance Metrics

- Execution Time: Total query processing duration
- Resolver Count: Number of resolver calls per query
- Database Queries: SQL/NoSQL operations generated
- Memory Usage: Heap allocation during execution
- Cache Hit Rate: Effectiveness of caching layers
- Network Round Trips: External API calls made

### Common Performance Issues

#### N+1 Query Problems

- DataLoader implementation
- Batch loading strategies
- Request-scoped caching
- Error handling

#### Over-fetching and Under-fetching

- Field analysis
- Query complexity measurement
- Depth limiting
- Query allowlisting

#### Inefficient Pagination

- Cursor-based pagination
- Relay-style connections
- Offset-based pagination limitations

## Performance Optimization Strategies

### DataLoader Implementation

- Batch multiple requests into single database query
- Cache results within single request
- Error handling for partial failures

### Query Complexity Analysis

- Query complexity limits
- Depth limiting
- Cost analysis
- Resource protection

### Caching Strategies

- Response caching
- Field-level caching
- Multi-level caching
- Cache invalidation

### Database Query Optimization

- Database projections
- Field selection analysis
- Query optimization
- Index usage

## Best Practices

- Focus on measurable improvements with proper before/after benchmarks
- Always validate that optimizations don't compromise data consistency or security
- Implement monitoring and alerting to catch performance regressions early
- Maintain optimal GraphQL API performance in production

Your performance optimizations should focus on measurable improvements with proper before/after benchmarks. Always validate that optimizations don't compromise data consistency or security. Implement monitoring and alerting to catch performance regressions early and maintain optimal GraphQL API performance in production.

