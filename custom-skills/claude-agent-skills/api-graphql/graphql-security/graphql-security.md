---
name: graphql-security
description: This skill provides expertise in GraphQL API security and authorization. This skill should be used for GraphQL security audits, authorization implementation, query validation, or protection against GraphQL-specific attacks. Focuses on defense in depth.
enforcement_level: CRITICAL
violation_consequence: GraphQL APIs may be vulnerable to attacks, unauthorized access may occur, or data may be exposed
---

# GraphQL Security

This skill provides comprehensive guidance for securing GraphQL APIs against common vulnerabilities and implementing robust authorization patterns. It emphasizes defense in depth.

## ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT PROCEED WITH GRAPHQL SECURITY IMPLEMENTATION UNTIL YOU:**

```python
# MANDATORY security checks:
# 1. Query validation and complexity limits
# 2. Authorization implementation
# 3. Rate limiting and DoS protection
# 4. Input sanitization
# 5. Error handling without information leakage
```

**DID YOU COMPLETE SECURITY CHECKS? Yes / No**

IF NO → STOP, complete checks first
IF YES → Output: "✅ Security checks complete" and continue

---

## Core Security Principles

- Query Validation: Prevent malicious or expensive queries
- Authorization: Field-level and operation-level access control
- Rate Limiting: Protect against abuse and DoS attacks
- Input Sanitization: Validate and sanitize all user inputs
- Error Handling: Prevent information leakage through errors
- Audit Logging: Track security-relevant operations

## Common GraphQL Security Vulnerabilities

### Query Depth and Complexity Attacks

- Depth bomb attacks
- Complexity exploitation
- Protection with depth limiting
- Query complexity analysis

### Information Disclosure

- Introspection in production
- Error message leakage
- Schema exposure
- Internal details in errors

## Authorization Implementation

### Field-Level Authorization

- Authorization directives
- Role-based access
- Resource ownership
- Permission checks

### Context-Based Authorization

- Resolver context
- User permissions
- Row-level security
- Data filtering

### Row-Level Security (RLS)

- Database-level security
- User-based filtering
- Department-based access
- Role-based filtering

## Input Validation and Sanitization

### Schema-Level Validation

- Custom scalars
- Input constraints
- Type validation
- Format validation

### Input Sanitization

- XSS prevention
- Injection prevention
- Data cleaning
- Safe handling

## Rate Limiting and DoS Protection

### Query-Based Rate Limiting

- IP-based limiting
- User-based limiting
- Operation-based limiting
- Slow down mechanisms

### Query Allowlisting

- Production allowlisting
- Query hashing
- Security validation
- Operation control

### Timeout Protection

- Query timeouts
- Resolver timeouts
- Connection timeouts
- Resource limits

## Best Practices

- Comprehensive, tested, and monitored security implementations
- Follow the principle of defense in depth with multiple security layers
- Assume that any publicly accessible GraphQL endpoint will be probed for vulnerabilities
- Regular security audits and penetration testing are essential

Your security implementations should be comprehensive, tested, and monitored. Always follow the principle of defense in depth with multiple security layers and assume that any publicly accessible GraphQL endpoint will be probed for vulnerabilities. Regular security audits and penetration testing are essential for maintaining a secure GraphQL API in production.

