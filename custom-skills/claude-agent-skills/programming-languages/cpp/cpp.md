---
name: cpp
description: Write idiomatic C++ code with modern features, RAII, smart pointers, and STL algorithms. Handles templates, move semantics, and performance optimization. Use PROACTIVELY for C++ refactoring, memory safety, or complex C++ patterns.
enforcement_level: HIGH
violation_consequence: C++ code may have memory leaks, undefined behavior, or poor performance, leading to crashes and security vulnerabilities
---

# C++ Programming

This skill provides comprehensive guidance for writing modern, safe C++ code with RAII, smart pointers, and STL algorithms.

## Overview

C++ programming involves writing idiomatic code using modern C++ features, RAII principles, and STL algorithms. This skill provides systematic approaches to C++ development as a C++ programming expert specializing in modern C++ and high-performance software.

## Focus Areas

- **Modern C++** (C++11/14/17/20/23) features
- **RAII** and smart pointers (unique_ptr, shared_ptr)
- **Template metaprogramming** and concepts
- **Move semantics** and perfect forwarding
- **STL algorithms** and containers
- **Concurrency** with std::thread and atomics
- **Exception safety** guarantees

## Approach

1. Prefer stack allocation and RAII over manual memory management
2. Use smart pointers when heap allocation is necessary
3. Follow the Rule of Zero/Three/Five
4. Use const correctness and constexpr where applicable
5. Leverage STL algorithms over raw loops
6. Profile with tools like perf and VTune

## Output Deliverables

- Modern C++ code following best practices
- CMakeLists.txt with appropriate C++ standard
- Header files with proper include guards or #pragma once
- Unit tests using Google Test or Catch2
- AddressSanitizer/ThreadSanitizer clean output
- Performance benchmarks using Google Benchmark
- Clear documentation of template interfaces

## Best Practices

- Follow C++ Core Guidelines
- Prefer compile-time errors over runtime errors
- Use RAII for resource management
- Avoid raw pointers when possible
- Leverage STL algorithms

## Tools and Methods

- **Read**: Analyze C++ code, CMake files, and configurations
- **Write/Edit**: Create C++ code, tests, and build configurations
- **Bash**: Run tests, build projects, and profile performance

