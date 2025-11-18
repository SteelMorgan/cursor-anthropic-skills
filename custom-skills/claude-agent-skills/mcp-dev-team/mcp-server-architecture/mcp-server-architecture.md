---
name: mcp-server-architecture
description: This skill provides expertise in MCP server architecture and implementation. This skill should be used for designing servers, implementing transport layers, tool definitions, completion support, or protocol compliance. Focuses on production-ready implementations following MCP specification.
enforcement_level: CRITICAL
violation_consequence: MCP servers may be non-compliant with protocol, insecure, or fail in production, causing system failures
---

# MCP Server Architecture

This skill provides comprehensive guidance for designing and implementing MCP (Model Context Protocol) servers following the full server lifecycle from design to deployment. It emphasizes protocol compliance, security, and performance.

## ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT PROCEED WITH MCP SERVER DEVELOPMENT UNTIL YOU:**

```python
# MANDATORY validations:
# 1. Review MCP specification (2025-06-18)
# 2. Identify domain and use cases
# 3. Plan transport layers (stdio/HTTP)
# 4. Design security and authentication
# 5. Plan error handling and validation
```

**DID YOU COMPLETE VALIDATIONS? Yes / No**

IF NO → STOP, validate first
IF YES → Output: "✅ MCP server prerequisites validated" and continue

---

## 🔒 MCP Server Development Gate System

### Gate 1: Requirements Analysis ✋ STOP HERE FIRST
- **Action**: Understand domain and use cases before designing server architecture
- **Verify**: All requirements documented, use cases clear
- **Confirmation**: "Gate 1 cleared: Requirements analyzed"

### Gate 2: Tool Interface Design ✋ STOP HERE SECOND
- **Action**: Create intuitive, well-documented tools with proper annotations and completion support
- **Verify**: JSON Schema validation, tool annotations, completion support
- **Confirmation**: "Gate 2 cleared: Tool interfaces designed"

### Gate 3: Transport Layer Implementation ✋ STOP HERE THIRD
- **Action**: Set up both stdio and HTTP transports with proper error handling and fallbacks
- **Verify**: JSON-RPC 2.0 implementation, SSE fallback, transport negotiation
- **Confirmation**: "Gate 3 cleared: Transport layers implemented"

### Gate 4: Security Implementation ✋ STOP HERE FOURTH
- **Action**: Implement proper authentication, session management, and input validation
- **Verify**: Session IDs secure, Origin header validation, input validation
- **Confirmation**: "Gate 4 cleared: Security implemented"

### Gate 5: Performance Optimization ✋ STOP HERE FIFTH
- **Action**: Use connection pooling, caching, and efficient data structures
- **Verify**: Connection pooling configured, caching implemented, efficient algorithms
- **Confirmation**: "Gate 5 cleared: Performance optimized"

## 🚦 Final MCP Server Checkpoint

**Verify all gates cleared:**

```
✅ MCP SERVER STATUS
- Gate 1: [CLEARED / BLOCKED]
- Gate 2: [CLEARED / BLOCKED]
- Gate 3: [CLEARED / BLOCKED]
- Gate 4: [CLEARED / BLOCKED]
- Gate 5: [CLEARED / BLOCKED]

Ready to deploy: [YES / NO]
```

**IF ANY GATE BLOCKED:**
- ❌ STOP immediately
- Complete: [Missing gate]
- Then: Resume from next gate

## Core Architecture Competencies

### Protocol and Transport Implementation

- Implement servers using JSON-RPC 2.0 over stdio and Streamable HTTP transports
- Provide SSE fallback for legacy clients
- Ensure proper transport negotiation
- Handle both GET and POST methods appropriately

### Tool, Resource & Prompt Design

- Define tools with proper JSON Schema validation
- Implement annotations (read-only, destructive, idempotent, open-world)
- Include audio and image responses when appropriate
- Incorporate tool annotations into UI prompts

### Completion Support

- Declare the `completions` capability
- Implement the `completion/complete` endpoint
- Provide intelligent argument value suggestions

### Batching

- Support JSON-RPC batching
- Allow multiple requests in a single HTTP call
- Improve performance through batching

### Session Management

- Implement secure, non-deterministic session IDs
- Bind session IDs to user identity
- Validate the `Origin` header on all Streamable HTTP requests
- Use durable objects or stateful services for session persistence
- Avoid exposing session IDs to clients

## Development Standards

Follow these standards rigorously:

- Use the latest MCP specification (2025-06-18) as reference
- Implement servers in TypeScript using `@modelcontextprotocol/sdk` (≥1.10.0) or Python with comprehensive type hints
- Enforce JSON Schema validation for all tool inputs and outputs
- Incorporate tool annotations into UI prompts for better user experience
- Provide single `/mcp` endpoints handling both GET and POST methods appropriately
- Include audio, image, and embedded resources in tool results when relevant
- Implement caching, connection pooling, and multi-region deployment patterns
- Document all server capabilities including `tools`, `resources`, `prompts`, `completions`, and `batching`

## Advanced Implementation Practices

Implement these advanced features:

- Use durable objects or stateful services for session persistence while avoiding exposure of session IDs to clients
- Adopt intentional tool budgeting by grouping related API calls into high-level tools
- Support macros or chained prompts for complex workflows
- Shift security left by scanning dependencies and implementing SBOMs
- Provide verbose logging during development and reduce noise in production
- Ensure logs flow to stderr (never stdout) to maintain protocol integrity
- Containerize servers using multi-stage Docker builds for optimal deployment
- Use semantic versioning and maintain comprehensive release notes and changelogs

## Implementation Approach

When creating or enhancing an MCP server:

1. **Analyze Requirements**: Thoroughly understand the domain and use cases before designing the server architecture
2. **Design Tool Interfaces**: Create intuitive, well-documented tools with proper annotations and completion support
3. **Implement Transport Layers**: Set up both stdio and HTTP transports with proper error handling and fallbacks
4. **Ensure Security**: Implement proper authentication, session management, and input validation
5. **Optimize Performance**: Use connection pooling, caching, and efficient data structures
6. **Test Thoroughly**: Create comprehensive test suites covering all transport modes and edge cases
7. **Document Extensively**: Provide clear documentation for server setup, configuration, and usage

## Code Quality Standards

Ensure all code:
- Follows TypeScript/Python best practices with full type coverage
- Includes comprehensive error handling with meaningful error messages
- Uses async/await patterns for non-blocking operations
- Implements proper resource cleanup and connection management
- Includes inline documentation for complex logic
- Follows consistent naming conventions and code organization

## Security Considerations

Always:
- Validate all inputs against JSON Schema before processing
- Implement rate limiting and request throttling
- Use environment variables for sensitive configuration
- Avoid exposing internal implementation details in error messages
- Implement proper CORS policies for HTTP endpoints
- Use secure session management without exposing session IDs

## 🚨 CRITICAL - Violation Consequences

```yaml
ENFORCEMENT_LEVEL: CRITICAL
VIOLATION_CONSEQUENCE: PROTOCOL_NON_COMPLIANCE_AND_SYSTEM_FAILURE
SCOPE: All MCP server development and deployment
```

**IF you skip protocol compliance or security:**
- ❌ Server will fail protocol validation
- ❌ Security vulnerabilities may be exploited
- ❌ System integration failures
- ❌ Production deployment blocked
- ❌ User trust compromised

**MCP PROTOCOL COMPLIANCE IS NOT OPTIONAL**

When asked to create or modify an MCP server, provide complete, production-ready implementations that follow all these standards and best practices. Proactively identify potential issues and suggest improvements to ensure the server is robust, secure, and performant.

