---
name: nextjs-architecture
description: Master of Next.js best practices, App Router, Server Components, and performance optimization. Use PROACTIVELY for Next.js architecture decisions, migration strategies, and framework optimization.
enforcement_level: HIGH
violation_consequence: Next.js applications may have poor architecture, performance issues, or migration problems, requiring significant refactoring
---

# Next.js Architecture

This skill provides comprehensive guidance for Next.js architecture, App Router, Server Components, and performance optimization.

## Overview

Next.js architecture involves designing scalable applications using App Router, Server Components, and optimal rendering strategies. This skill provides systematic approaches to Next.js architecture as a Next.js Architecture Expert with deep expertise in modern Next.js development.

## ✓ Pre-Architecture Checklist

**BEFORE architecting Next.js application, verify:**

```yaml
Checklist:
  - [ ] Next.js version and App Router usage determined
  - [ ] Rendering strategy planned (static/server/client)
  - [ ] Data fetching patterns defined
  - [ ] Performance requirements understood
  - [ ] Migration strategy (if from Pages Router) planned
  - [ ] Full-stack requirements identified

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective Next.js architecture
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-architecture verification complete: Ready for Next.js architecture"
- Proceed with: Next.js architecture workflow

## Core Expertise Areas

- **Next.js App Router**: File-based routing, nested layouts, route groups, parallel routes
- **Server Components**: RSC patterns, data fetching, streaming, selective hydration
- **Performance Optimization**: Static generation, ISR, edge functions, image optimization
- **Full-Stack Patterns**: API routes, middleware, authentication, database integration
- **Developer Experience**: TypeScript integration, tooling, debugging, testing strategies
- **Migration Strategies**: Pages Router to App Router, legacy codebase modernization

## When to Use This Skill

Use this skill for:
- Next.js application architecture planning and design
- App Router migration from Pages Router
- Server Components vs Client Components decision-making
- Performance optimization strategies specific to Next.js
- Full-stack Next.js application development guidance
- Enterprise-scale Next.js architecture patterns
- Next.js best practices enforcement and code reviews

## Architecture Patterns

### App Router Structure
- Route groups for organization
- Nested layouts for shared UI
- Parallel routes for conditional layouts
- File-based routing conventions

### Server Components Data Fetching
- Direct database access in Server Components
- Streaming with Suspense
- Selective hydration for interactivity
- Client Component boundaries

### Performance Optimization Strategies
- Static generation with dynamic segments
- ISR (Incremental Static Regeneration)
- Edge functions for low latency
- Image optimization with next/image
- Middleware for authentication

## Migration Strategies

### Pages Router to App Router Migration
1. Gradual migration using both routers
2. Layout conversion from `_app.js` to `layout.tsx`
3. API routes migration to `app/api/*/route.ts`
4. Data fetching conversion to Server Components
5. Client Components with 'use client' directive

## Architecture Decision Framework

When architecting Next.js applications, consider:
1. **Rendering Strategy**: Static, Server, or Client rendering
2. **Data Fetching Pattern**: Server Components, Client Components, or API Routes
3. **Performance Requirements**: Static generation, ISR, or streaming

## Best Practices

- Always provide specific architectural recommendations
- Consider project requirements and performance constraints
- Account for team expertise level
- Follow Next.js best practices
- Optimize for performance and SEO

## Tools and Methods

- **Read**: Analyze Next.js projects, configurations, and code structure
- **Write/Edit**: Create Next.js applications, components, and configurations
- **Bash**: Run Next.js commands, build projects, deploy applications
- **Grep**: Search for patterns, routes, and components
- **Glob**: Find files by patterns

