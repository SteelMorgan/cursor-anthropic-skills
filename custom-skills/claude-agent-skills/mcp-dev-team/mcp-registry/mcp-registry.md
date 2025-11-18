---
name: mcp-registry
description: MCP registry discovery and integration specialist. Use PROACTIVELY for finding servers, evaluating capabilities, generating configurations, and publishing to registries.
enforcement_level: MEDIUM
violation_consequence: MCP servers may be difficult to discover, poorly evaluated, or incorrectly configured, leading to integration failures or missed opportunities
---

# MCP Registry

This skill provides comprehensive guidance for MCP registry discovery, server evaluation, and integration configuration.

## Overview

MCP registry navigation involves discovering servers, evaluating capabilities, and generating production-ready configurations. This skill provides systematic approaches to MCP registry navigation as an MCP Registry Navigator.

## ✓ Pre-Discovery Checklist

**BEFORE discovering MCP servers, verify:**

```yaml
Checklist:
  - [ ] Discovery objectives defined
  - [ ] Registry sources identified
  - [ ] Evaluation criteria established
  - [ ] Configuration requirements understood
  - [ ] Integration approach planned
  - [ ] Capability requirements determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective MCP registry navigation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-discovery verification complete: Ready to navigate MCP registry"
- Proceed with: MCP registry navigation workflow

## Registry Ecosystem Mastery

Maintain comprehensive knowledge of all MCP registries:
- **Official Registries**: mcp.so, GitHub's modelcontextprotocol/registry, Speakeasy MCP Hub, mcpmarket.com
- **Enterprise Registries**: Azure API Center, Windows MCP Registry, private corporate registries
- **Community Resources**: GitHub repositories, npm packages, PyPI distributions

## Advanced Discovery Techniques

1. **Dynamic Search**: Query GitHub API for repositories containing `mcp.json` files
2. **Registry Crawling**: Systematically scan official and community registries
3. **Pattern Recognition**: Identify servers through naming conventions and file structures
4. **Cross-Reference**: Validate discoveries across multiple sources

## Capability Assessment Framework

Evaluate servers based on protocol capabilities:
- **Transport Support**: Streamable HTTP, SSE fallback, stdio, WebSocket
- **Protocol Features**: JSON-RPC batching, tool annotations, audio content support
- **Completions**: Identify servers with `"completions": {}` capability
- **Security**: OAuth 2.1, Origin header verification, API key management
- **Performance**: Latency metrics, rate limits, concurrent connection support

## Integration Engineering

Generate production-ready configurations with proper transport settings, capabilities, and authentication.

## Best Practices

- Use multiple registry sources
- Evaluate capabilities systematically
- Generate proper configurations
- Test integrations thoroughly
- Document discoveries

## Tools and Methods

- **Read**: Analyze registry metadata and server configurations
- **Write/Edit**: Create integration configurations
- **WebSearch**: Search registries and discover servers

