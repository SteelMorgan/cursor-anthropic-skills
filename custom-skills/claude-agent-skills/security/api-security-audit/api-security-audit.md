---
name: api-security-audit
description: This skill provides expertise in API security auditing. This skill should be used for REST API security audits, authentication vulnerabilities, authorization flaws, injection attacks, or compliance validation. Focuses on OWASP API Top 10.
enforcement_level: CRITICAL
violation_consequence: API vulnerabilities may remain undetected, leading to data breaches or unauthorized access
---

# API Security Audit

This skill provides comprehensive guidance for identifying, analyzing, and resolving security vulnerabilities in REST APIs. It emphasizes OWASP API Top 10 compliance.

## ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT PROCEED WITH API SECURITY AUDIT UNTIL YOU:**

```python
# MANDATORY security checks:
# 1. Review authentication mechanisms (JWT, OAuth2)
# 2. Check authorization and access controls
# 3. Test for injection vulnerabilities
# 4. Verify data protection and encryption
# 5. Validate security headers and rate limiting
```

**DID YOU COMPLETE SECURITY CHECKS? Yes / No**

IF NO → STOP, complete checks first
IF YES → Output: "✅ Security checks complete" and continue

---

## Core Expertise Areas

### Authentication Security

- JWT vulnerabilities
- Token management
- Session security
- Password policies

### Authorization Flaws

- RBAC issues
- Privilege escalation
- Access control bypasses
- Role-based access

### Injection Attacks

- SQL injection prevention
- NoSQL injection prevention
- Command injection prevention
- Input validation

### Data Protection

- Sensitive data exposure
- Encryption at rest and in transit
- Secure transmission
- Data masking

### API Security Standards

- OWASP API Top 10
- Security headers
- Rate limiting
- CORS configuration

### Compliance

- GDPR requirements for APIs
- HIPAA requirements
- PCI DSS requirements
- Industry standards

## Security Audit Checklist

### Authentication & Authorization

- Secure JWT implementation
- Token expiration and refresh
- Proper authorization checks
- Role-based access control

### Input Validation & Sanitization

- Input validation middleware
- SQL injection prevention
- XSS prevention
- Command injection prevention

### Security Headers

- Content Security Policy
- CORS configuration
- Rate limiting
- Security headers

## Best Practices

- Always provide specific, actionable security recommendations
- Include code examples and remediation steps
- Focus on OWASP API Top 10 vulnerabilities
- Test authentication and authorization thoroughly
- Validate all inputs

Always provide specific, actionable security recommendations with code examples and remediation steps when conducting API security audits.

