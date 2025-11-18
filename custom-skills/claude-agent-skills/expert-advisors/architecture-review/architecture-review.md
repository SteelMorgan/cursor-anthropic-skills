---
name: architecture-review
description: Use this skill to review code for architectural consistency and patterns. Specializes in SOLID principles, proper layering, and maintainability.
enforcement_level: HIGH
violation_consequence: Code may violate architectural principles, leading to technical debt, poor maintainability, or scalability issues
---

# Architecture Review

This skill provides comprehensive guidance for reviewing code through an architectural lens, ensuring consistency with established patterns and principles.

## Overview

Architecture review involves analyzing code changes for architectural integrity, pattern adherence, and long-term maintainability. This skill provides systematic approaches to architectural review as an expert software architect focused on maintaining architectural integrity.

## ✓ Pre-Review Checklist

**BEFORE starting architecture review, verify:**

```yaml
Checklist:
  - [ ] Code changes identified and accessible
  - [ ] System architecture understood
  - [ ] Architectural patterns established
  - [ ] Review scope defined
  - [ ] Related components identified
  - [ ] Context of changes understood

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective architecture review
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-review verification complete: Ready to review architecture"
- Proceed with: Architecture review workflow

## Core Expertise Areas

- **Pattern Adherence**: Verifying code follows established architectural patterns (e.g., MVC, Microservices, CQRS)
- **SOLID Compliance**: Checking for violations of SOLID principles (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion)
- **Dependency Analysis**: Ensuring proper dependency direction and avoiding circular dependencies
- **Abstraction Levels**: Verifying appropriate abstraction without over-engineering
- **Future-Proofing**: Identifying potential scaling or maintenance issues

## When to Use This Skill

Use this skill for:
- Reviewing structural changes in a pull request
- Designing new services or components
- Refactoring code to improve its architecture
- Ensuring API modifications are consistent with the existing design

## Review Process

1. **Map the change**: Understand the change within the overall system architecture
2. **Identify boundaries**: Analyze the architectural boundaries being crossed
3. **Check for consistency**: Ensure the change is consistent with existing patterns
4. **Evaluate modularity**: Assess the impact on system modularity and coupling
5. **Suggest improvements**: Recommend architectural improvements if needed

## Focus Areas

- **Service Boundaries**: Clear responsibilities and separation of concerns
- **Data Flow**: Coupling between components and data consistency
- **Domain-Driven Design**: Consistency with the domain model (if applicable)
- **Performance**: Implications of architectural decisions on performance
- **Security**: Security boundaries and data validation points

## Output Format

Provide a structured review with:
- **Architectural Impact**: Assessment of the change's impact (High, Medium, Low)
- **Pattern Compliance**: A checklist of relevant architectural patterns and their adherence
- **Violations**: Specific violations found, with explanations
- **Recommendations**: Recommended refactoring or design changes
- **Long-Term Implications**: The long-term effects of the changes on maintainability and scalability

## SOLID Principles Checklist

- **Single Responsibility**: Each class/component has one reason to change
- **Open/Closed**: Open for extension, closed for modification
- **Liskov Substitution**: Subtypes must be substitutable for their base types
- **Interface Segregation**: Clients should not depend on interfaces they don't use
- **Dependency Inversion**: Depend on abstractions, not concretions

## Common Architectural Patterns

- **Layered Architecture**: Clear separation between presentation, business, and data layers
- **Microservices**: Service boundaries, communication patterns, data consistency
- **CQRS**: Command Query Responsibility Segregation patterns
- **Event-Driven**: Event sourcing and event-driven architecture
- **Hexagonal Architecture**: Ports and adapters pattern

## Best Practices

- Good architecture enables change - flag anything that makes future changes harder
- Focus on long-term maintainability over short-term convenience
- Ensure clear boundaries and responsibilities
- Avoid tight coupling between components
- Consider scalability and performance implications
- Maintain consistency with existing patterns

## Tools and Methods

- **Read**: Analyze code structure, dependencies, and architectural patterns
- **Write/Edit**: Suggest architectural improvements and refactoring
- **Grep**: Search for pattern violations and architectural inconsistencies

