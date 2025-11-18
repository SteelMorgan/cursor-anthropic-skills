---
name: supabase-schema
description: This skill provides expertise in Supabase database schema design. This skill should be used for database schema design, migration planning, or RLS policy architecture. Focuses on PostgreSQL and Row Level Security.
enforcement_level: HIGH
violation_consequence: Database schemas may be poorly designed, migrations may fail, or RLS policies may be insecure
---

# Supabase Schema Architecture

This skill provides comprehensive guidance for PostgreSQL database design, migration strategies, and Row Level Security (RLS) implementation in Supabase.

## Overview

Supabase schema design involves creating normalized database schemas, planning safe migrations, and implementing comprehensive RLS policies. This skill provides systematic approaches to schema architecture.

## Focus Areas

### Schema Design

- Normalized database schemas
- Table relationships and indexes
- Foreign key constraints
- Efficient data types and storage

### Migration Management

- Safe, reversible database migrations
- Migration sequences and dependencies
- Rollback strategies
- Production impact validation

### RLS Policy Architecture

- Comprehensive Row Level Security policies
- Role-based access control
- Policy performance optimization
- Security without breaking functionality

## Standards and Metrics

### Database Design

- **Normalization**: 3NF minimum, denormalize only for performance
- **Naming**: snake_case for tables/columns, consistent prefixes
- **Indexing**: Query response time < 50ms for common operations
- **Constraints**: All business rules enforced at database level

### RLS Policies

- **Coverage**: 100% of tables with sensitive data must have RLS
- **Performance**: Policy execution overhead < 10ms
- **Testing**: Every policy must have positive and negative test cases
- **Documentation**: Clear policy descriptions and use cases

### Migration Quality

- **Atomicity**: All migrations wrapped in transactions
- **Reversibility**: Every migration has tested rollback
- **Safety**: No data loss, backward compatibility maintained
- **Performance**: Migration execution time < 5 minutes

## Best Practices

- Always provide specific SQL code examples
- Include migration scripts and comprehensive testing procedures
- Focus on production-ready solutions with proper error handling
- Test RLS policies thoroughly
- Document all schema decisions

Always provide specific SQL code examples, migration scripts, and comprehensive testing procedures. Focus on production-ready solutions with proper error handling and monitoring.

