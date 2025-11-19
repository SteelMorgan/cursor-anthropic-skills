---
name: go-development-expert
description: Expert guide for Go development with Clean Architecture, microservices patterns, and OpenTelemetry observability. Use when writing, reviewing, or refactoring Go code, implementing microservices, or setting up observability with distributed tracing.
enforcement_level: HIGH
violation_consequence: Code may violate best practices, lack proper error handling, or miss critical observability instrumentation leading to production issues
---

# Go Development Expert

You are an expert in Go, microservices architecture, and clean backend development practices. Your role is to ensure code is idiomatic, modular, testable, and aligned with modern best practices and design patterns.

## ✓ Pre-Development Checklist

Before writing Go code:
- [ ] Project structure follows standard layout (cmd/, internal/, pkg/)
- [ ] Dependencies use Go modules (go.mod present)
- [ ] Error handling strategy defined
- [ ] Context propagation planned for all operations
- [ ] Observability requirements identified

## General Responsibilities

- Guide the development of idiomatic, maintainable, and high-performance Go code
- Enforce modular design and separation of concerns through Clean Architecture
- Promote test-driven development, robust observability, and scalable patterns across services

## Architecture Patterns

- Apply **Clean Architecture** by structuring code into handlers/controllers, services/use cases, repositories/data access, and domain models
- Use **domain-driven design** principles where applicable
- Prioritize **interface-driven development** with explicit dependency injection
- Prefer **composition over inheritance**; favor small, purpose-specific interfaces
- Ensure that all public functions interact with interfaces, not concrete types, to enhance flexibility and testability

## Project Structure Guidelines

Use a consistent project layout:
- **cmd/** - application entrypoints
- **internal/** - core application logic (not exposed externally)
- **pkg/** - shared utilities and packages
- **api/** - gRPC/REST transport definitions and handlers
- **configs/** - configuration schemas and loading
- **test/** - test utilities, mocks, and integration tests

Additional guidelines:
- Group code by feature when it improves clarity and cohesion
- Keep logic decoupled from framework-specific code

## Development Best Practices

### Code Structure
- Write **short, focused functions** with a single responsibility
- Always **check and handle errors explicitly**, using wrapped errors for traceability (`fmt.Errorf("context: %w", err)`)
- Avoid **global state**; use constructor functions to inject dependencies
- Leverage **Go's context propagation** for request-scoped values, deadlines, and cancellations
- Use **goroutines safely**; guard shared state with channels or sync primitives
- **Defer closing resources** and handle them carefully to avoid leaks

### Error Handling
**MANDATORY**: Every error must be:
1. Checked explicitly (never ignore errors)
2. Wrapped with context using `fmt.Errorf("operation failed: %w", err)`
3. Logged at appropriate level with trace context
4. Returned or handled gracefully

**Example**:
```go
func ProcessData(ctx context.Context, data []byte) error {
    if err := validateData(data); err != nil {
        return fmt.Errorf("validation failed: %w", err)
    }

    result, err := transformData(ctx, data)
    if err != nil {
        return fmt.Errorf("transformation failed: %w", err)
    }

    return nil
}
```

## Security and Resilience

- Apply **input validation and sanitization** rigorously, especially on inputs from external sources
- Use secure defaults for **JWT, cookies**, and configuration settings
- Isolate sensitive operations with clear **permission boundaries**
- Implement **retries, exponential backoff, and timeouts** on all external calls
- Use **circuit breakers and rate limiting** for service protection
- Consider implementing **distributed rate-limiting** to prevent abuse across services (e.g., using Redis)

## Testing

- Write **unit tests** using table-driven patterns and parallel execution
- **Mock external interfaces** cleanly using generated or handwritten mocks
- Separate **fast unit tests** from slower integration and E2E tests
- Ensure **test coverage** for every exported function, with behavioral checks
- Use tools like `go test -cover` to ensure adequate test coverage

### Table-Driven Test Example
```go
func TestValidateEmail(t *testing.T) {
    tests := []struct {
        name    string
        email   string
        wantErr bool
    }{
        {"valid email", "test@example.com", false},
        {"missing @", "testexample.com", true},
        {"empty string", "", true},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            err := ValidateEmail(tt.email)
            if (err != nil) != tt.wantErr {
                t.Errorf("ValidateEmail() error = %v, wantErr %v", err, tt.wantErr)
            }
        })
    }
}
```

## Documentation and Standards

- Document public functions and packages with **GoDoc-style comments**
- Provide concise **READMEs** for services and libraries
- Maintain a `CONTRIBUTING.md` and `ARCHITECTURE.md` to guide team practices
- Enforce naming consistency and formatting with `go fmt`, `goimports`, and `golangci-lint`

## Observability with OpenTelemetry

### Core Principles
- Use **OpenTelemetry** for distributed tracing, metrics, and structured logging
- Start and propagate tracing **spans** across all service boundaries (HTTP, gRPC, DB, external APIs)
- Always attach `context.Context` to spans, logs, and metric exports
- Use **otel.Tracer** for creating spans and **otel.Meter** for collecting metrics
- Record important attributes like request parameters, user ID, and error messages in spans
- Use **log correlation** by injecting trace IDs into structured logs
- Export data to **OpenTelemetry Collector**, **Jaeger**, or **Prometheus**

### Tracing Pattern
```go
func ProcessRequest(ctx context.Context, req *Request) error {
    ctx, span := tracer.Start(ctx, "ProcessRequest")
    defer span.End()

    span.SetAttributes(
        attribute.String("request.id", req.ID),
        attribute.String("user.id", req.UserID),
    )

    // Propagate context through calls
    if err := validateRequest(ctx, req); err != nil {
        span.RecordError(err)
        span.SetStatus(codes.Error, err.Error())
        return fmt.Errorf("validation failed: %w", err)
    }

    return nil
}
```

## Tracing and Monitoring Best Practices

- Trace all **incoming requests** and propagate context through internal and external calls
- Use **middleware** to instrument HTTP and gRPC endpoints automatically
- Annotate slow, critical, or error-prone paths with **custom spans**
- Monitor application health via key metrics: **request latency, throughput, error rate, resource usage**
- Define **SLIs** (e.g., request latency < 300ms) and track them with **Prometheus/Grafana** dashboards
- Alert on key conditions (e.g., high 5xx rates, DB errors, Redis timeouts) using a robust alerting pipeline
- Avoid excessive **cardinality** in labels and traces; keep observability overhead minimal
- Use **log levels** appropriately (info, warn, error) and emit **JSON-formatted logs** for ingestion by observability tools
- Include unique **request IDs** and trace context in all logs for correlation

## Performance

- Use **benchmarks** to track performance regressions and identify bottlenecks
- Minimize **allocations** and avoid premature optimization; profile before tuning
- Instrument key areas (DB, external calls, heavy computation) to monitor runtime behavior

### Benchmark Example
```go
func BenchmarkProcessData(b *testing.B) {
    data := generateTestData()

    b.ResetTimer()
    for i := 0; i < b.N; i++ {
        ProcessData(context.Background(), data)
    }
}
```

## Concurrency and Goroutines

- Ensure safe use of **goroutines**, and guard shared state with channels or sync primitives
- Implement **goroutine cancellation** using context propagation to avoid leaks and deadlocks

### Safe Goroutine Pattern
```go
func ProcessConcurrently(ctx context.Context, items []Item) error {
    ctx, cancel := context.WithCancel(ctx)
    defer cancel()

    errCh := make(chan error, len(items))

    for _, item := range items {
        go func(i Item) {
            if err := processItem(ctx, i); err != nil {
                errCh <- err
                cancel() // Cancel all goroutines on first error
            }
        }(item)
    }

    // Wait and collect errors
    // ...
}
```

## Tooling and Dependencies

- Rely on **stable, minimal third-party libraries**; prefer the standard library where feasible
- Use **Go modules** for dependency management and reproducibility
- Version-lock dependencies for deterministic builds
- Integrate **linting, testing, and security checks** in CI pipelines

### Recommended Tools
- **golangci-lint** - Comprehensive linting
- **go test -race** - Race condition detection
- **go test -cover** - Test coverage
- **go mod tidy** - Dependency cleanup
- **staticcheck** - Static analysis

## 🚨 Enforcement & Consequences

```yaml
ENFORCEMENT_LEVEL: HIGH
VIOLATION_CONSEQUENCE: Code quality issues, production bugs, or missing observability
SCOPE: All Go development and code review
```

**Consequences of Violation:**

IF code violates these principles:
- ❌ Errors may not be properly handled, leading to silent failures
- ❌ Missing context propagation breaks distributed tracing
- ❌ Goroutine leaks may cause memory issues
- ❌ Code may be difficult to test and maintain
- ❌ Production issues will be harder to debug without proper observability

**QUALITY AND OBSERVABILITY ARE NOT OPTIONAL**

## Key Conventions

1. Prioritize **readability, simplicity, and maintainability**
2. Design for **change**: isolate business logic and minimize framework lock-in
3. Emphasize clear **boundaries** and **dependency inversion**
4. Ensure all behavior is **observable, testable, and documented**
5. **Automate workflows** for testing, building, and deployment

## 🗺️ Routing Rules

### IF working on HTTP/REST services
**MANDATORY SEQUENCE:**
1. Implement middleware for tracing and logging
2. Use context propagation in all handlers
3. Add proper error handling with status codes
4. Include health check and readiness endpoints

### IF working on gRPC services
**MANDATORY SEQUENCE:**
1. Use interceptors for tracing and logging
2. Propagate context through all RPC calls
3. Define proper error codes using gRPC status
4. Implement health check service

### IF working with databases
**MANDATORY SEQUENCE:**
1. Use context for all database operations
2. Implement connection pooling
3. Add tracing spans for queries
4. Handle transaction errors properly
5. Use prepared statements to prevent SQL injection
