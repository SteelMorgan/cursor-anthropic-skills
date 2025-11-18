---
name: security-auditing-code
description: This skill provides expertise in reviewing code for vulnerabilities and ensuring OWASP compliance. This skill should be used for security reviews, authentication flows, or vulnerability fixes. Focuses on practical fixes over theoretical risks.
enforcement_level: CRITICAL
violation_consequence: Security vulnerabilities may remain undetected, leading to data breaches, unauthorized access, or system compromise
---

# Security Auditing (Code)

This skill provides comprehensive guidance for reviewing code for vulnerabilities, implementing secure authentication, and ensuring OWASP compliance. It emphasizes practical fixes over theoretical risks.

## ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT PROCEED WITH CODE REVIEW UNTIL YOU:**

```python
# MANDATORY security checks:
# 1. Review code for OWASP Top 10 vulnerabilities
# 2. Check authentication and authorization implementation
# 3. Verify input validation and sanitization
# 4. Review encryption and secure communication
# 5. Check security headers and CSP policies
```

**DID YOU COMPLETE SECURITY CHECKS? Yes / No**

IF NO → STOP, check first
IF YES → Output: "✅ Security checks complete" and continue

---

## 🔒 Security Audit Gate System

### Gate 1: Authentication/Authorization Review ✋ STOP HERE FIRST
- **Action**: Review JWT, OAuth2, SAML implementation
- **Verify**: Secure token handling, proper authorization checks
- **Confirmation**: "Gate 1 cleared: Auth mechanisms reviewed"

### Gate 2: OWASP Top 10 Check ✋ STOP HERE SECOND
- **Action**: Check for injection, broken auth, sensitive data exposure
- **Verify**: All OWASP Top 10 vulnerabilities addressed
- **Confirmation**: "Gate 2 cleared: OWASP compliance verified"

### Gate 3: Input Validation ✋ STOP HERE THIRD
- **Action**: Verify all inputs validated and sanitized
- **Verify**: SQL injection prevention, XSS protection
- **Confirmation**: "Gate 3 cleared: Input validation verified"

### Gate 4: Encryption Review ✋ STOP HERE FOURTH
- **Action**: Check encryption at rest and in transit
- **Verify**: TLS/SSL, data encryption, key management
- **Confirmation**: "Gate 4 cleared: Encryption verified"

## 🚦 Final Security Checkpoint

**Verify all gates cleared:**

```
✅ SECURITY AUDIT STATUS
- Gate 1: [CLEARED / BLOCKED]
- Gate 2: [CLEARED / BLOCKED]
- Gate 3: [CLEARED / BLOCKED]
- Gate 4: [CLEARED / BLOCKED]

Ready to proceed: [YES / NO]
```

**IF ANY GATE BLOCKED:**
- ❌ STOP immediately
- Complete: [Missing gate]
- Then: Resume from next gate

## Focus Areas

### Authentication/Authorization

- JWT (JSON Web Tokens)
- OAuth2
- SAML
- Session management
- Password policies

### OWASP Top 10 Vulnerability Detection

- Injection attacks
- Broken authentication
- Sensitive data exposure
- XML external entities (XXE)
- Broken access control
- Security misconfiguration
- Cross-site scripting (XSS)
- Insecure deserialization
- Using components with known vulnerabilities
- Insufficient logging and monitoring

### Secure API Design

- CORS configuration
- Rate limiting
- Input validation
- Secure error handling
- Authentication checks

### Input Validation and SQL Injection Prevention

- Parameterized queries
- Input sanitization
- Type checking
- Whitelist validation
- Output encoding

### Encryption Implementation

- Data at rest encryption
- Data in transit (TLS/SSL)
- Key management
- Algorithm selection

### Security Headers and CSP Policies

- Content Security Policy (CSP)
- X-Frame-Options
- X-Content-Type-Options
- Strict-Transport-Security (HSTS)
- Referrer-Policy
- Permissions-Policy

## Approach

1. **Defense in depth**: Multiple security layers
2. **Principle of least privilege**: Minimum necessary permissions
3. **Never trust user input**: Validate everything
4. **Fail securely**: No information leakage
5. **Regular dependency scanning**: Automated vulnerability scanning

## Output Format

Provide:
- Security audit report with severity levels
- Secure implementation code with comments
- Authentication flow diagrams
- Security checklist for the specific feature
- Recommended security headers configuration
- Test cases for security scenarios

## 🚨 CRITICAL - Violation Consequences

```yaml
ENFORCEMENT_LEVEL: CRITICAL
VIOLATION_CONSEQUENCE: SECURITY_BREACH_RISK
SCOPE: All code security reviews
```

**IF you skip security checks:**
- ❌ Security vulnerabilities remain undetected
- ❌ Data breaches may occur
- ❌ Unauthorized access possible
- ❌ System compromise risk

**SECURITY VALIDATION IS NOT OPTIONAL**

## Best Practices

- Focus on practical fixes over theoretical risks
- Include OWASP references
- Provide specific code examples
- Test security scenarios
- Document security decisions

Focus on practical fixes over theoretical risks. Include OWASP references.

