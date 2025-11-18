---
name: api-documentation
description: Create OpenAPI/Swagger specs, generate SDKs, and write developer documentation. Handles versioning, examples, and interactive docs. Use PROACTIVELY for API documentation or client library generation.
enforcement_level: HIGH
violation_consequence: API documentation may be incomplete, inaccurate, or difficult to use, leading to poor developer experience and integration issues
---

# API Documentation

This skill provides comprehensive guidance for creating developer-focused API documentation, OpenAPI specifications, and SDK generation.

## Overview

API documentation involves creating clear, accurate, and comprehensive documentation for APIs that enables developers to successfully integrate and use the API. This skill provides systematic approaches to API documentation as an API documentation specialist focused on developer experience.

## ✓ Pre-Documentation Checklist

**BEFORE starting API documentation, verify:**

```yaml
Checklist:
  - [ ] API endpoints and methods identified
  - [ ] Request/response schemas defined
  - [ ] Authentication methods understood
  - [ ] Error codes and responses documented
  - [ ] Code examples prepared
  - [ ] Versioning strategy determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective API documentation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-documentation verification complete: Ready to document API"
- Proceed with: API documentation workflow

## Focus Areas

- **OpenAPI 3.0/Swagger specification** writing
- **SDK generation** and client libraries
- **Interactive documentation** (Postman/Insomnia)
- **Versioning strategies** and migration guides
- **Code examples** in multiple languages
- **Authentication and error** documentation

## Approach

1. **Document as you build** - not after
2. **Real examples** over abstract descriptions
3. **Show both success and error cases**
4. **Version everything** including docs
5. **Test documentation accuracy**

## Output Deliverables

### Complete OpenAPI Specification
- All endpoints with methods (GET, POST, PUT, DELETE)
- Request/response schemas with validation rules
- Authentication requirements
- Error responses with codes and messages
- Query parameters and path variables

### Request/Response Examples
- Examples with all fields populated
- Multiple scenarios (success, error, edge cases)
- Code examples in multiple languages (JavaScript, Python, cURL)
- Authentication examples

### Authentication Setup Guide
- Authentication methods (API keys, OAuth, JWT)
- Step-by-step setup instructions
- Token generation and refresh
- Security best practices

### Error Code Reference
- Complete list of error codes
- Error message formats
- Solutions and troubleshooting
- Retry strategies

### SDK Usage Examples
- Installation instructions
- Basic usage examples
- Advanced patterns
- Common use cases

### Postman Collection
- Pre-configured requests
- Environment variables
- Test scripts
- Documentation integration

## Best Practices

- Focus on developer experience
- Include curl examples and common use cases
- Keep documentation up-to-date with code changes
- Provide interactive examples where possible
- Test all examples before publishing
- Use consistent formatting and structure
- Include rate limiting and usage guidelines

## Tools and Methods

- **Read**: Analyze API code, existing documentation, and examples
- **Write/Edit**: Create OpenAPI specs, documentation files, and examples
- **Bash**: Generate SDKs, test API endpoints, validate documentation

## Common Documentation Patterns

### OpenAPI Structure
```yaml
openapi: 3.0.0
info:
  title: API Name
  version: 1.0.0
paths:
  /endpoint:
    get:
      summary: Description
      parameters: [...]
      responses:
        200:
          description: Success
          content:
            application/json:
              schema: {...}
```

### Code Examples
- Include examples in multiple languages
- Show both simple and complex use cases
- Provide copy-paste ready code
- Include error handling examples

### Versioning
- Semantic versioning for APIs
- Migration guides between versions
- Deprecation notices
- Backward compatibility documentation

