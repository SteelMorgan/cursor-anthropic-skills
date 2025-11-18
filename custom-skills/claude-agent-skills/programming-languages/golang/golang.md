---
name: golang
description: Write idiomatic Go code with goroutines, channels, and interfaces. Optimizes concurrency, implements Go patterns, and ensures proper error handling. Use PROACTIVELY for Go refactoring, concurrency issues, or performance optimization.
enforcement_level: HIGH
violation_consequence: Go code may have race conditions, poor error handling, or non-idiomatic patterns, leading to bugs and maintenance issues
---

# Go Programming

This skill provides comprehensive guidance for writing idiomatic, concurrent Go code with proper error handling and performance optimization.

## Overview

Go programming involves writing simple, clear, concurrent code using goroutines, channels, and interfaces. This skill provides systematic approaches to Go development as a Go expert specializing in concurrent, performant code.

## Focus Areas

- **Concurrency patterns** (goroutines, channels, select)
- **Interface design** and composition
- **Error handling** and custom error types
- **Performance optimization** and pprof profiling
- **Testing** with table-driven tests and benchmarks
- **Module management** and vendoring

## Approach

1. Simplicity first - clear is better than clever
2. Composition over inheritance via interfaces
3. Explicit error handling, no hidden magic
4. Concurrent by design, safe by default
5. Benchmark before optimizing

## Output Deliverables

- Idiomatic Go code following effective Go guidelines
- Concurrent code with proper synchronization
- Table-driven tests with subtests
- Benchmark functions for performance-critical code
- Error handling with wrapped errors and context
- Clear interfaces and struct composition

## Best Practices

- Prefer standard library
- Minimize external dependencies
- Include go.mod setup
- Use interfaces for flexibility
- Handle errors explicitly

## Tools and Methods

- **Read**: Analyze Go code, go.mod, and project structure
- **Write/Edit**: Create Go code, tests, and documentation
- **Bash**: Run go commands, tests, and benchmarks

