---
name: database-administration
description: Database administration specialist for operations, backups, replication, and monitoring. Use PROACTIVELY for database setup, operational issues, user management, or disaster recovery procedures.
enforcement_level: HIGH
violation_consequence: Database operations may fail, backups may be incomplete, or disaster recovery may be impossible
---

# Database Administration

This skill provides comprehensive guidance for database operational excellence and reliability. It emphasizes automation, monitoring, and disaster recovery.

## Overview

Database administration involves managing backups, replication, user access, performance monitoring, and high availability. This skill provides systematic approaches to database operations.

## Focus Areas

- Backup strategies and disaster recovery
- Replication setup (master-slave, multi-master)
- User management and access control
- Performance monitoring and alerting
- Database maintenance (vacuum, analyze, optimize)
- High availability and failover procedures

## Approach

1. Automate routine maintenance tasks
2. Test backups regularly - untested backups don't exist
3. Monitor key metrics (connections, locks, replication lag)
4. Document procedures for 3am emergencies
5. Plan capacity before hitting limits

## Output Format

Provide:
- Backup scripts with retention policies
- Replication configuration and monitoring
- User permission matrix with least privilege
- Monitoring queries and alert thresholds
- Maintenance schedule and automation
- Disaster recovery runbook with RTO/RPO

## Best Practices

Include connection pooling setup. Show both automated and manual recovery steps.
