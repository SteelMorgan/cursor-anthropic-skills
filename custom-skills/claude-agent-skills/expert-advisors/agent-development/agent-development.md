---
name: agent-development
description: Use this skill when creating specialized Claude Code agents for the claude-code-templates components system. Specializes in agent design, prompt engineering, domain expertise modeling, and agent best practices.
enforcement_level: HIGH
violation_consequence: Agents may be poorly designed, lack clear expertise boundaries, or fail to integrate properly with the Claude Code system
---

# Agent Development

This skill provides comprehensive guidance for creating, designing, and optimizing specialized Claude Code agents for the claude-code-templates system.

## Overview

Agent development involves creating specialized agents with clear expertise boundaries, proper prompt engineering, and domain knowledge modeling. This skill provides systematic approaches to agent creation as an Agent Expert specializing in agent architecture and design.

## ✓ Pre-Development Checklist

**BEFORE creating an agent, verify:**

```yaml
Checklist:
  - [ ] Domain and expertise boundaries identified
  - [ ] Target user needs and use cases analyzed
  - [ ] Core competencies determined
  - [ ] Knowledge scope and limitations planned
  - [ ] Integration with existing agents considered
  - [ ] Agent type and pattern selected

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective agent development
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-development verification complete: Ready to create agent"
- Proceed with: Agent development workflow

## Agent Structure

### Standard Agent Format
```markdown
---
name: agent-name
description: Use this agent when [specific use case]. Specializes in [domain areas]. Examples: <example>Context: [situation description] user: '[user request]' assistant: '[response using agent]' <commentary>[reasoning for using this agent]</commentary></example> [additional examples]
color: [color]
---

You are a [Domain] specialist focusing on [specific expertise areas]. Your expertise covers [key areas of knowledge].

Your core expertise areas:
- **[Area 1]**: [specific capabilities]
- **[Area 2]**: [specific capabilities]
- **[Area 3]**: [specific capabilities]

## When to Use This Agent

Use this agent for:
- [Use case 1]
- [Use case 2]
- [Use case 3]

## [Domain-Specific Sections]

### [Category 1]
[Detailed information, code examples, best practices]

### [Category 2]
[Implementation guidance, patterns, solutions]

Always provide [specific deliverables] when working in this domain.
```

## Agent Types

### 1. Technical Specialization Agents
- Frontend framework experts (React, Vue, Angular)
- Backend technology specialists (Node.js, Python, Go)
- Database experts (SQL, NoSQL, Graph databases)
- DevOps and infrastructure specialists

### 2. Domain Expertise Agents
- Security specialists (API, Web, Mobile)
- Performance optimization experts
- Accessibility and UX specialists
- Testing and quality assurance experts

### 3. Industry-Specific Agents
- E-commerce development specialists
- Healthcare application experts
- Financial technology specialists
- Educational technology experts

### 4. Workflow and Process Agents
- Code review specialists
- Architecture design experts
- Project management specialists
- Documentation and technical writing experts

## Agent Creation Process

### 1. Domain Analysis
When creating a new agent:
- Identify the specific domain and expertise boundaries
- Analyze the target user needs and use cases
- Determine the agent's core competencies
- Plan the knowledge scope and limitations
- Consider integration with existing agents

### 2. Agent Design Patterns

#### Technical Expert Agent Pattern
- Clear expertise boundaries
- Comprehensive domain knowledge
- Practical code examples
- Best practices and patterns
- Implementation guidance

#### Domain Specialist Agent Pattern
- Domain-specific knowledge areas
- Process and standard guidelines
- Implementation approaches
- Relevant categories based on domain

### 3. Prompt Engineering Best Practices

#### Clear Expertise Boundaries
- Define specific capabilities clearly
- Distinguish related but distinct knowledge
- Include complementary skills
- State limitations explicitly

#### Practical Examples and Context
- Include 3-4 realistic usage examples
- Provide detailed situation descriptions
- Show appropriate response strategies
- Include clear reasoning for agent selection

### 4. Code Examples and Templates
- Real-world examples with comments
- Best practice patterns
- Implementation checklists
- Common pitfalls to avoid

## Agent Naming and Organization

### Naming Conventions
- **Technical Agents**: `[technology]-expert.md` (e.g., `react-expert.md`)
- **Domain Agents**: `[domain]-specialist.md` (e.g., `security-specialist.md`)
- **Process Agents**: `[process]-expert.md` (e.g., `code-review-expert.md`)

### Color Coding System
- **Frontend**: blue, cyan, teal
- **Backend**: green, emerald, lime
- **Security**: red, crimson, rose
- **Performance**: yellow, amber, orange
- **Testing**: purple, violet, indigo
- **DevOps**: gray, slate, stone

### Description Format
- Use specific trigger conditions
- List 2-3 key specialization areas
- Include 2-3 realistic examples with context
- Provide clear reasoning for agent selection

## Quality Assurance for Agents

### Agent Testing Checklist
1. **Expertise Validation**
   - Verify domain knowledge accuracy
   - Test example implementations
   - Validate best practices recommendations
   - Check for up-to-date information

2. **Prompt Engineering**
   - Test trigger conditions and examples
   - Verify appropriate agent selection
   - Validate response quality and relevance
   - Check for clear expertise boundaries

3. **Integration Testing**
   - Test with Claude Code CLI system
   - Verify component installation process
   - Test agent invocation and context
   - Validate cross-agent compatibility

### Documentation Standards
- Include 3-4 realistic usage examples
- Provide comprehensive code examples
- Document limitations and boundaries clearly
- Include best practices and common patterns
- Add troubleshooting guidance

## Agent Creation Workflow

### 1. Create the Agent File
- **Location**: `cli-tool/components/agents/`
- **Naming**: Use kebab-case: `frontend-security.md`
- **Format**: YAML frontmatter + Markdown content

### 2. Required YAML Frontmatter Structure
```yaml
---
name: frontend-security
description: Use this agent when securing frontend applications. Specializes in XSS prevention, CSP implementation, and secure authentication flows. Examples: <example>Context: User needs to secure React app user: 'My React app is vulnerable to XSS attacks' assistant: 'I'll use the frontend-security agent to analyze and implement XSS protections' <commentary>Frontend security issues require specialized expertise</commentary></example>
color: red
---
```

**Required Frontmatter Fields:**
- `name`: Unique identifier (kebab-case, matches filename)
- `description`: Clear description with 2-3 usage examples in specific format
- `color`: Display color (red, green, blue, yellow, magenta, cyan, white, gray)

### 3. Agent Content Structure
- Core expertise areas with specific capabilities
- When to use this agent section
- Domain-specific implementation examples
- Best practices and patterns
- Specific deliverables and quality standards

## Tools and Methods

- **Read**: Analyze existing agents, domain requirements, and user needs
- **Write/Edit**: Create agent files with proper structure and examples
- **Bash**: Test agent installation and CLI integration

## Best Practices

When creating specialized agents, always:
- Create files in `cli-tool/components/agents/` directory
- Follow the YAML frontmatter format exactly
- Include 2-3 realistic usage examples in description
- Use appropriate color coding for the domain
- Provide comprehensive domain expertise
- Include practical, actionable examples
- Test with the CLI installation command
- Implement clear expertise boundaries

If you encounter requirements outside agent creation scope, clearly state the limitation and suggest appropriate resources or alternative approaches.

