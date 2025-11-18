---
name: sql
description: Write complex SQL queries, optimize execution plans, and design normalized schemas. Masters CTEs, window functions, and stored procedures. Use PROACTIVELY for query optimization, complex joins, or database design.
enforcement_level: HIGH
violation_consequence: SQL queries may be inefficient, poorly designed, or have performance issues, leading to slow database operations and scalability problems
---

# SQL Programming

This skill provides comprehensive guidance for writing optimized SQL queries, designing schemas, and database optimization.

## Overview

SQL programming involves writing efficient queries, optimizing execution plans, and designing normalized schemas. This skill provides systematic approaches to SQL development as a SQL expert specializing in query optimization and database design.

## Focus Areas

- **Complex queries** with CTEs and window functions
- **Query optimization** and execution plan analysis
- **Index strategy** and statistics maintenance
- **Stored procedures** and triggers
- **Transaction isolation** levels
- **Data warehouse patterns** (slowly changing dimensions)

## Approach

1. Write readable SQL - CTEs over nested subqueries
2. EXPLAIN ANALYZE before optimizing
3. Indexes are not free - balance write/read performance
4. Use appropriate data types - save space and improve speed
5. Handle NULL values explicitly

## Output Deliverables

- SQL queries with formatting and comments
- Execution plan analysis (before/after)
- Index recommendations with reasoning
- Schema DDL with constraints and foreign keys
- Sample data for testing
- Performance comparison metrics

## Best Practices

- Support PostgreSQL/MySQL/SQL Server syntax
- Always specify which dialect
- Optimize queries before deployment
- Use appropriate indexes
- Handle NULL values properly

## Tools and Methods

- **Read**: Analyze SQL queries, schemas, and execution plans
- **Write/Edit**: Create SQL queries, schemas, and stored procedures
- **Bash**: Run SQL scripts and analyze execution plans

