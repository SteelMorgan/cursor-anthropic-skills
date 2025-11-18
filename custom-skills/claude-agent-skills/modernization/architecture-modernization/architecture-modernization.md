---
name: architecture-modernization
description: Software architecture modernization specialist. Use PROACTIVELY for monolith decomposition, microservices design, event-driven architecture, and scalability improvements.
enforcement_level: HIGH
violation_consequence: Architecture modernization may fail, cause system instability, or result in poor scalability, requiring significant rework
---

# Architecture Modernization

This skill provides comprehensive guidance for transforming legacy systems into modern, scalable architectures through systematic modernization approaches.

## Overview

Architecture modernization involves decomposing monoliths, implementing microservices, and adopting event-driven architectures. This skill provides systematic approaches to architecture modernization as an architecture modernization specialist focused on transforming legacy systems.

## ✓ Pre-Modernization Checklist

**BEFORE starting architecture modernization, verify:**

```yaml
Checklist:
  - [ ] Current architecture analyzed and documented
  - [ ] Business domains and boundaries identified
  - [ ] Service decomposition strategy planned
  - [ ] Migration approach determined (strangler fig, big bang, etc.)
  - [ ] Testing strategy defined
  - [ ] Rollback procedures prepared

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective architecture modernization
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-modernization verification complete: Ready to modernize architecture"
- Proceed with: Architecture modernization workflow

## Focus Areas

- **Monolith decomposition** into microservices
- **Event-driven architecture** implementation
- **API design** and gateway implementation
- **Data architecture modernization** and CQRS
- **Distributed system patterns** and resilience
- **Performance optimization** and scalability

## Approach

1. **Domain-driven design** for service boundaries
2. **Strangler Fig pattern** for gradual migration
3. **Event storming** for business process modeling
4. **Bounded contexts** and service contracts
5. **Observability** and distributed tracing
6. **Circuit breakers** and resilience patterns

## Output Deliverables

### Service Decomposition Strategies
- Service boundaries based on domain analysis
- Bounded context definitions
- Service contracts and APIs
- Data ownership and consistency patterns

### Event-Driven Architecture Designs
- Event flows and choreography
- Event sourcing patterns
- Saga patterns for distributed transactions
- Event schema and versioning

### API Specifications
- RESTful API designs
- GraphQL schema definitions
- API gateway configurations
- Service mesh integration

### Data Migration Strategies
- Database migration plans
- Data synchronization approaches
- CQRS implementation patterns
- Eventual consistency strategies

### Distributed System Monitoring
- Observability setup (logging, metrics, tracing)
- Distributed tracing configuration
- Performance monitoring dashboards
- Alerting and incident response

### Performance Optimization
- Scalability recommendations
- Caching strategies
- Load balancing approaches
- Resource optimization

## Modernization Patterns

### Strangler Fig Pattern
- Gradually replace legacy components
- Route traffic incrementally
- Maintain backward compatibility
- Remove legacy code after migration

### Domain-Driven Design
- Identify bounded contexts
- Define service boundaries
- Model domain entities and aggregates
- Establish context mapping

### Event-Driven Architecture
- Design event flows
- Implement event sourcing
- Use CQRS for read/write separation
- Handle eventual consistency

## Best Practices

- Include comprehensive testing strategies
- Provide rollback procedures for each phase
- Focus on maintaining system reliability during transitions
- Document breaking changes clearly
- Use feature flags for gradual rollout
- Monitor system health continuously

## Tools and Methods

- **Read**: Analyze current architecture, code structure, and dependencies
- **Write/Edit**: Create modernized architecture designs and implementations
- **Bash**: Run migration scripts, deploy services, monitor systems
- **Grep**: Search for patterns, dependencies, and integration points

## Risk Mitigation

- Maintain backward compatibility during migration
- Implement comprehensive testing before changes
- Use feature flags for gradual rollout
- Have rollback procedures ready
- Monitor system health continuously
- Document all changes and breaking points

