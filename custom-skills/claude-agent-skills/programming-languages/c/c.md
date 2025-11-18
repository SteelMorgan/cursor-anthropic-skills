---
name: c
description: Write efficient C code with proper memory management, pointer arithmetic, and system calls. Handles embedded systems, kernel modules, and performance-critical code. Use PROACTIVELY for C optimization, memory issues, or system programming.
enforcement_level: HIGH
violation_consequence: C code may have memory leaks, buffer overflows, or undefined behavior, leading to crashes and security vulnerabilities
---

# C Programming

This skill provides comprehensive guidance for writing efficient, safe C code with proper memory management and system programming.

## Overview

C programming involves writing efficient code with proper memory management, pointer arithmetic, and system calls. This skill provides systematic approaches to C development as a C programming expert specializing in systems programming and performance.

## Focus Areas

- **Memory management** (malloc/free, memory pools)
- **Pointer arithmetic** and data structures
- **System calls** and POSIX compliance
- **Embedded systems** and resource constraints
- **Multi-threading** with pthreads
- **Debugging** with valgrind and gdb

## Approach

1. No memory leaks - every malloc needs free
2. Check all return values, especially malloc
3. Use static analysis tools (clang-tidy)
4. Minimize stack usage in embedded contexts
5. Profile before optimizing

## Output Deliverables

- C code with clear memory ownership
- Makefile with proper flags (-Wall -Wextra)
- Header files with proper include guards
- Unit tests using CUnit or similar
- Valgrind clean output demonstration
- Performance benchmarks if applicable

## Best Practices

- Follow C99/C11 standards
- Include error handling for all system calls
- Use static analysis tools
- Test memory management thoroughly
- Document memory ownership

## Tools and Methods

- **Read**: Analyze C code, Makefiles, and configurations
- **Write/Edit**: Create C code, tests, and build files
- **Bash**: Compile, test, and profile C programs

