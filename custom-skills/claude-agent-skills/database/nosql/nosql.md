---
name: nosql
description: This skill provides expertise in NoSQL databases for MongoDB, Redis, Cassandra, and document/key-value stores. This skill should be used for schema design, data modeling, performance optimization, or NoSQL architecture decisions. Focuses on appropriate data modeling for each technology.
enforcement_level: HIGH
violation_consequence: NoSQL databases may be poorly designed, perform poorly, or fail to scale, leading to data loss or poor application performance
---

# NoSQL Database Specialist

This skill provides comprehensive guidance for document stores, key-value databases, column-family, and graph databases. It emphasizes appropriate data modeling for each technology.

## Overview

NoSQL database design involves choosing appropriate data models, optimizing for access patterns, and ensuring scalability. This skill provides systematic approaches to NoSQL architecture.

## Core NoSQL Technologies

### Document Databases

- **MongoDB**: Flexible documents, rich queries, horizontal scaling
- **CouchDB**: HTTP API, eventual consistency, offline-first design
- **Amazon DocumentDB**: MongoDB-compatible, managed service
- **Azure Cosmos DB**: Multi-model, global distribution, SLA guarantees

### Key-Value Stores

- **Redis**: In-memory, data structures, pub/sub, clustering
- **Amazon DynamoDB**: Managed, predictable performance, serverless
- **Apache Cassandra**: Wide-column, linear scalability, fault tolerance
- **Riak**: Eventually consistent, high availability, conflict resolution

### Graph Databases

- **Neo4j**: Native graph storage, Cypher query language
- **Amazon Neptune**: Managed graph service, Gremlin and SPARQL
- **ArangoDB**: Multi-model with graph capabilities

## Performance Optimization Strategies

### MongoDB Performance Tuning

- Efficient indexing strategy
- Aggregation pipeline optimization
- Connection pooling optimization
- Query optimization

### Redis Performance Patterns

- Pipeline operations to reduce network round trips
- Use appropriate data structures
- Memory optimization with compression
- Caching strategies

### Cassandra Data Modeling

- Time-series data modeling
- Partition key design
- Materialized views
- Query optimization

### DynamoDB Design Patterns

- Single-table design
- Global Secondary Indexes
- Local Secondary Indexes
- Conditional updates

## Best Practices

- Focus on appropriate data modeling for each NoSQL technology
- Consider access patterns, consistency requirements, and scalability needs
- Always include performance benchmarking and monitoring strategies
- Optimize for the specific database engine
- Test scalability assumptions

Focus on appropriate data modeling for each NoSQL technology, considering access patterns, consistency requirements, and scalability needs. Always include performance benchmarking and monitoring strategies.

