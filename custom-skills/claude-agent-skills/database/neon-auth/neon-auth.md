---
name: neon-auth
description: Neon Auth implementation specialist. Use PROACTIVELY for Stack Auth integration, user management setup, authentication flows, and security best practices with Neon database.
enforcement_level: HIGH
violation_consequence: Authentication may fail, user data may be insecure, or security vulnerabilities may be exposed
---

# Neon Auth

This skill provides comprehensive guidance for authentication implementation, user management, and security integration with Neon database and Stack Auth.

## Overview

Neon Auth involves integrating Stack Auth with Neon database for user management and authentication. This skill provides systematic approaches to secure authentication implementation.

## Work Process

### 1. Authentication Analysis
- Search for existing auth implementations
- Identify Stack Auth usage
- Check Neon Auth integration status

### 2. Implementation Focus
- Set up Stack Auth with Neon Auth integration
- Configure user management workflows
- Implement secure authentication patterns
- Handle user data synchronization

## Stack Auth Setup

### Initial Installation
```bash
npx @stackframe/init-stack@latest
```

### Environment Configuration
- `NEXT_PUBLIC_STACK_PROJECT_ID`
- `NEXT_PUBLIC_STACK_PUBLISHABLE_CLIENT_KEY`
- `STACK_SECRET_SERVER_KEY`
- `DATABASE_URL`

### Basic Integration
- Wrap app with StackProvider and StackTheme
- Configure server app instance
- Set up handler routes

## Neon Auth Database Schema

### Schema Structure
- `neon_auth` schema
- `users_sync` table with JSONB storage
- Indexes on deleted_at
- User data synchronization

### Database Integration Patterns
- Joining user data with application tables
- Filtering deleted users
- LEFT JOIN patterns
- User permission validation

## Security Best Practices

- Always filter out deleted users: `WHERE deleted_at IS NULL`
- Use LEFT JOIN when relating to `neon_auth.users_sync`
- Never create foreign keys to the auth schema
- Handle user deletion gracefully in application logic
- Validate user permissions on every protected operation

## Page Protection Middleware

- Middleware for route protection
- Redirect to sign-in for unauthorized users
- Configurable matcher patterns

## Best Practices

Focus on secure authentication patterns and proper user data synchronization. Always validate user permissions and handle edge cases gracefully.

