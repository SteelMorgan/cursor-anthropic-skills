---
name: security-auditing
description: This skill provides expertise in application security auditing and secure coding practices. This skill should be used when reviewing code for vulnerabilities, implementing secure authentication, ensuring OWASP compliance, handling JWT/OAuth2, configuring CORS/CSP, or implementing encryption. Focuses on practical security fixes over theoretical risks.
enforcement_level: CRITICAL
violation_consequence: Security vulnerabilities may remain undetected, leading to data breaches, unauthorized access, or system compromise
---

# Security Auditing

This skill provides comprehensive guidance for conducting security audits, implementing secure authentication, and ensuring compliance with security standards. It emphasizes practical fixes and OWASP best practices.

## ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT PROCEED WITH SECURITY AUDIT UNTIL YOU:**

```python
# MANDATORY validations:
# 1. Verify codebase access and permissions
# 2. Identify technology stack and framework
# 3. Check for existing security tools and configurations
# 4. Review deployment and infrastructure setup
```

**DID YOU COMPLETE VALIDATIONS? Yes / No**

IF NO → STOP, validate first
IF YES → Output: "✅ Security audit prerequisites validated" and continue

---

## 🔒 Security Audit Gate System

### Gate 1: Environment Analysis ✋ STOP HERE FIRST
- **Action**: Identify technology stack, framework, and deployment environment
- **Verify**: Existing security tools, configurations, and infrastructure
- **Confirmation**: "Gate 1 cleared: Environment analyzed"

### Gate 2: Dependency Security Check ✋ STOP HERE SECOND
- **Action**: Scan all dependencies for known vulnerabilities
- **Verify**: Outdated packages with security issues, dependency sources
- **Confirmation**: "Gate 2 cleared: Dependencies scanned"

### Gate 3: Authentication & Authorization Review ✋ STOP HERE THIRD
- **Action**: Review authentication mechanisms, session management, authorization controls
- **Verify**: Proper password policies, secure session handling, access restrictions
- **Confirmation**: "Gate 3 cleared: Auth mechanisms reviewed"

### Gate 4: Input Validation & Data Protection ✋ STOP HERE FOURTH
- **Action**: Check input validation, SQL injection prevention, XSS protection, encryption
- **Verify**: All user inputs validated, sensitive data encrypted, secure communication
- **Confirmation**: "Gate 4 cleared: Input validation and data protection verified"

### Gate 5: Infrastructure & Configuration Security ✋ STOP HERE FIFTH
- **Action**: Review containerization security, CI/CD pipeline, cloud configuration, network security
- **Verify**: Secure configurations, proper permissions, network isolation
- **Confirmation**: "Gate 5 cleared: Infrastructure security reviewed"

## 🚦 Final Security Checkpoint

**Verify all gates cleared:**

```
✅ SECURITY AUDIT STATUS
- Gate 1: [CLEARED / BLOCKED]
- Gate 2: [CLEARED / BLOCKED]
- Gate 3: [CLEARED / BLOCKED]
- Gate 4: [CLEARED / BLOCKED]
- Gate 5: [CLEARED / BLOCKED]

Ready to generate security report: [YES / NO]
```

**IF ANY GATE BLOCKED:**
- ❌ STOP immediately
- Complete: [Missing gate]
- Then: Resume from next gate

## Focus Areas

### 1. Authentication/Authorization

Expertise in:
- **JWT (JSON Web Tokens)**: Token generation, validation, refresh strategies
- **OAuth2**: Authorization flows, token management, client types
- **SAML**: Enterprise authentication integration
- **Session management**: Secure session storage, expiration, invalidation
- **Password policies**: Hashing (bcrypt, Argon2), complexity requirements, reset flows

### 2. OWASP Top 10 Vulnerability Detection

Identify and remediate:
- Injection attacks (SQL, NoSQL, Command)
- Broken authentication
- Sensitive data exposure
- XML external entities (XXE)
- Broken access control
- Security misconfiguration
- Cross-site scripting (XSS)
- Insecure deserialization
- Using components with known vulnerabilities
- Insufficient logging and monitoring

### 3. Secure API Design

Design APIs with:
- Proper CORS configuration
- Rate limiting and throttling
- Input validation and sanitization
- Secure error handling (no information leakage)
- Authentication and authorization checks
- Request size limits

### 4. Input Validation and SQL Injection Prevention

Implement:
- Parameterized queries (never string concatenation)
- Input sanitization and validation
- Type checking and constraints
- Whitelist validation where possible
- Output encoding to prevent XSS

### 5. Encryption Implementation

Ensure:
- **Data at rest**: Encryption for sensitive data storage
- **Data in transit**: TLS/SSL for all communications
- **Key management**: Secure key storage and rotation
- **Algorithm selection**: Use current, secure algorithms

### 6. Security Headers and CSP Policies

Configure:
- Content Security Policy (CSP)
- X-Frame-Options
- X-Content-Type-Options
- Strict-Transport-Security (HSTS)
- Referrer-Policy
- Permissions-Policy

## Approach

Follow these security principles:

1. **Defense in depth** - Multiple security layers
   - Network security
   - Application security
   - Data security
   - Access controls

2. **Principle of least privilege**
   - Users have minimum necessary permissions
   - Services run with minimal privileges
   - Database users with limited access

3. **Never trust user input** - Validate everything
   - Validate on client and server
   - Sanitize all inputs
   - Use parameterized queries
   - Encode outputs

4. **Fail securely** - No information leakage
   - Generic error messages for users
   - Detailed logs for administrators
   - No stack traces in production
   - No sensitive data in error responses

5. **Regular dependency scanning**
   - Automated vulnerability scanning
   - Regular updates
   - Monitor security advisories
   - Maintain SBOM (Software Bill of Materials)

## Output Deliverables

When conducting security audits, provide:

### Security Audit Report

Include:
- **Severity levels**: Critical, High, Medium, Low
- **Vulnerability descriptions**: What the issue is
- **Affected components**: Files, functions, endpoints
- **Impact assessment**: What could happen if exploited
- **Remediation steps**: How to fix the issue
- **Code examples**: Before/after code showing fixes

### Secure Implementation Code

Provide:
- Secure code examples with comments
- Best practice implementations
- OWASP references where applicable
- Testing recommendations

### Authentication Flow Diagrams

Create diagrams showing:
- Authentication flows (OAuth2, JWT, SAML)
- Token lifecycle
- Session management
- Authorization decision points

### Security Checklist

Provide checklist for:
- Authentication implementation
- Authorization checks
- Input validation
- Encryption requirements
- Security headers
- Logging and monitoring

### Recommended Security Headers Configuration

Include:
- Complete security headers setup
- CSP policy examples
- Configuration for different frameworks
- Testing recommendations

### Test Cases for Security Scenarios

Provide:
- Test cases for authentication
- Authorization test scenarios
- Input validation tests
- Security header verification
- Penetration testing scenarios

## Common Security Patterns

### JWT Implementation

```javascript
// Secure JWT generation
const token = jwt.sign(
  { userId, role },
  process.env.JWT_SECRET,
  { expiresIn: '1h', algorithm: 'HS256' }
);

// Secure JWT verification
const decoded = jwt.verify(token, process.env.JWT_SECRET);
```

### OAuth2 Authorization Flow

```
1. User requests access
2. Redirect to authorization server
3. User authenticates and authorizes
4. Authorization server returns code
5. Exchange code for access token
6. Use access token for API calls
```

### Input Validation

```javascript
// Parameterized query (SQL injection prevention)
const query = 'SELECT * FROM users WHERE id = ?';
db.query(query, [userId]);

// Input sanitization
const sanitized = validator.escape(userInput);
```

### Security Headers

```javascript
app.use(helmet({
  contentSecurityPolicy: {
    directives: {
      defaultSrc: ["'self'"],
      scriptSrc: ["'self'", "'unsafe-inline'"],
      styleSrc: ["'self'", "'unsafe-inline'"]
    }
  },
  hsts: { maxAge: 31536000 }
}));
```

## OWASP Top 10 Reference

Always reference OWASP Top 10 when identifying vulnerabilities:

1. **A01:2021 – Broken Access Control**
2. **A02:2021 – Cryptographic Failures**
3. **A03:2021 – Injection**
4. **A04:2021 – Insecure Design**
5. **A05:2021 – Security Misconfiguration**
6. **A06:2021 – Vulnerable and Outdated Components**
7. **A07:2021 – Identification and Authentication Failures**
8. **A08:2021 – Software and Data Integrity Failures**
9. **A09:2021 – Security Logging and Monitoring Failures**
10. **A10:2021 – Server-Side Request Forgery (SSRF)**

## 🚨 CRITICAL - Violation Consequences

```yaml
ENFORCEMENT_LEVEL: CRITICAL
VIOLATION_CONSEQUENCE: SECURITY_BREACH_RISK
SCOPE: All security audit and implementation tasks
```

**IF you skip security checks or implement insecure code:**
- ❌ Security vulnerabilities remain undetected
- ❌ Data breaches may occur
- ❌ Unauthorized access possible
- ❌ System compromise risk
- ❌ Compliance violations
- ❌ User trust damage

**SECURITY VALIDATION IS NOT OPTIONAL**

## Best Practices

- **Start with threat modeling**: Identify potential threats
- **Use security frameworks**: Leverage proven security libraries
- **Regular audits**: Schedule periodic security reviews
- **Automated scanning**: Integrate security scanning in CI/CD
- **Security training**: Keep team updated on security practices
- **Incident response**: Plan for security incident handling
- **Compliance**: Ensure regulatory compliance (GDPR, HIPAA, etc.)

## Common Mistakes to Avoid

- ❌ Storing passwords in plain text
- ❌ Using weak encryption algorithms
- ❌ Exposing sensitive data in error messages
- ❌ Skipping input validation
- ❌ Using string concatenation for SQL queries
- ❌ Missing security headers
- ❌ Weak session management
- ❌ Insufficient logging
- ❌ Ignoring dependency vulnerabilities
- ❌ Overlooking API security

Focus on practical fixes over theoretical risks. Always include OWASP references.

