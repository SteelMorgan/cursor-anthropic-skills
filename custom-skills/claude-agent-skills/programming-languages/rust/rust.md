---
name: rust
description: Write idiomatic Rust with ownership patterns, lifetimes, and trait implementations. Masters async/await, safe concurrency, and zero-cost abstractions. Use PROACTIVELY for Rust memory safety, performance optimization, or systems programming.
enforcement_level: HIGH
violation_consequence: Rust code may have compilation errors, lifetime issues, or unsafe code misuse, leading to bugs and security vulnerabilities
---

# Rust Programming

This skill provides comprehensive guidance for writing safe, performant Rust code with ownership patterns and trait implementations.

## Overview

Rust programming involves writing idiomatic code using ownership, borrowing, lifetimes, and traits for safe systems programming. This skill provides systematic approaches to Rust development as a Rust expert specializing in safe, performant systems programming.

## Focus Areas

- **Ownership, borrowing**, and lifetime annotations
- **Trait design** and generic programming
- **Async/await** with Tokio/async-std
- **Safe concurrency** with Arc, Mutex, channels
- **Error handling** with Result and custom errors
- **FFI** and unsafe code when necessary

## Approach

1. Leverage the type system for correctness
2. Zero-cost abstractions over runtime checks
3. Explicit error handling - no panics in libraries
4. Use iterators over manual loops
5. Minimize unsafe blocks with clear invariants

## Output Deliverables

- Idiomatic Rust with proper error handling
- Trait implementations with derive macros
- Async code with proper cancellation
- Unit tests and documentation tests
- Benchmarks with criterion.rs
- Cargo.toml with feature flags

## Best Practices

- Follow clippy lints
- Include examples in doc comments
- Use Result for error handling
- Minimize unsafe code
- Leverage the type system

## Tools and Methods

- **Read**: Analyze Rust code, Cargo.toml, and configurations
- **Write/Edit**: Create Rust code, tests, and documentation
- **Bash**: Run cargo commands, tests, and benchmarks

