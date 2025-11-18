---
name: command-development
description: This skill provides expertise in CLI command development for the claude-code-templates system. This skill should be used when designing commands, implementing argument parsing, automating tasks, or applying CLI best practices. Focuses on production-ready command implementations.
enforcement_level: HIGH
violation_consequence: Commands may be poorly designed, insecure, or fail validation, requiring significant refactoring
---

# Command Development

This skill provides comprehensive guidance for creating, designing, and optimizing CLI commands for the claude-code-templates system. It covers command design patterns, argument parsing, task automation, and CLI best practices.

## Overview

CLI command development involves designing intuitive command interfaces that automate tasks, validate inputs, and provide clear feedback. This skill provides systematic approaches to command creation and optimization.

## ✓ Pre-Command Checklist

**BEFORE creating CLI command, verify:**

```yaml
Checklist:
  - [ ] Use case and user needs identified
  - [ ] Input requirements and argument structure analyzed
  - [ ] Output format and success criteria determined
  - [ ] Error handling and edge cases planned
  - [ ] Performance and scalability considered

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective command design
- Next step: Gather missing requirements before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-command verification complete: Ready to create command"
- Proceed with: Command creation workflow

## Command Structure

### Standard Command Format

```markdown
# Command Name

Brief description of what the command does and its primary use case.

## Task

I'll [action description] for $ARGUMENTS following [relevant standards/practices].

## Process

I'll follow these steps:

1. [Step 1 description]
2. [Step 2 description]
3. [Step 3 description]
4. [Final step description]

## [Specific sections based on command type]

### [Category 1]
- [Feature 1 description]
- [Feature 2 description]
- [Feature 3 description]

## Best Practices

### [Practice Category]
- [Best practice 1]
- [Best practice 2]
- [Best practice 3]

I'll adapt to your project's [tools/framework] and follow established patterns.
```

### Command Types

#### 1. Code Generation Commands
- Component generators (React, Vue, Angular)
- API endpoint generators
- Test file generators
- Configuration file generators

#### 2. Code Analysis Commands
- Code quality analyzers
- Security audit commands
- Performance profilers
- Dependency analyzers

#### 3. Build and Deploy Commands
- Build optimization commands
- Deployment automation
- Environment setup commands
- CI/CD pipeline generators

#### 4. Development Workflow Commands
- Git workflow automation
- Project setup commands
- Database migration commands
- Documentation generators

## Command Creation Process

### 1. Requirements Analysis

When creating a new command:
- Identify the target use case and user needs
- Analyze input requirements and argument structure
- Determine output format and success criteria
- Plan error handling and edge cases
- Consider performance and scalability

### 2. Command Design Patterns

#### Task-Oriented Commands

```markdown
# Task Automation Command

Automate [specific task] for $ARGUMENTS with [quality standards].

## Task

I'll automate [task description] including:

1. [Primary function]
2. [Secondary function]
3. [Validation and error handling]
4. [Output and reporting]

## Process

I'll follow these steps:

1. Analyze the target [files/components/system]
2. Identify [patterns/issues/opportunities]
3. Implement [solution/optimization/generation]
4. Validate results and provide feedback
```

#### Analysis Commands

```markdown
# Analysis Command

Analyze [target] for $ARGUMENTS and provide comprehensive insights.

## Task

I'll perform [analysis type] covering:

1. [Analysis area 1]
2. [Analysis area 2]
3. [Reporting and recommendations]

## Analysis Types

### [Category 1]
- [Analysis method 1]
- [Analysis method 2]
- [Analysis method 3]
```

### 3. Argument and Parameter Handling

#### File/Directory Arguments

```markdown
## Process

I'll follow these steps:

1. Validate input paths and file existence
2. Apply glob patterns for multi-file operations
3. Check file permissions and access rights
4. Process files with proper error handling
5. Generate comprehensive output and logs
```

#### Configuration Arguments

```markdown
## Configuration Options

The command accepts these parameters:
- **--config**: Custom configuration file path
- **--output**: Output directory or format
- **--verbose**: Enable detailed logging
- **--dry-run**: Preview changes without execution
- **--force**: Override safety checks
```

### 4. Error Handling and Validation

#### Input Validation

```markdown
## Validation Process

1. **File System Validation**
   - Verify file/directory existence
   - Check read/write permissions
   - Validate file formats and extensions

2. **Parameter Validation**
   - Validate argument combinations
   - Check configuration syntax
   - Ensure required dependencies exist

3. **Environment Validation**
   - Check system requirements
   - Validate tool availability
   - Verify network connectivity if needed
```

#### Error Recovery

```markdown
## Error Handling

### Recovery Strategies
- Graceful degradation for non-critical failures
- Automatic retry for transient errors
- Clear error messages with resolution steps
- Rollback mechanisms for destructive operations

### Logging and Reporting
- Structured error logs with context
- Progress indicators for long operations
- Summary reports with success/failure counts
- Recommendations for issue resolution
```

## Command Naming Conventions

### File Naming
- Use lowercase with hyphens: `generate-component.md`
- Be descriptive and action-oriented: `optimize-bundle.md`
- Include target type: `analyze-security.md`

### Command Names
- Use clear, imperative verbs: "Generate Component"
- Include target and action: "Optimize Bundle Size"
- Keep names concise but descriptive: "Security Analyzer"

## Command Creation Workflow

When creating new CLI commands:

### 1. Create the Command File
- **Location**: Always create new commands in `cli-tool/components/commands/`
- **Naming**: Use kebab-case: `optimize-images.md`
- **Format**: Markdown with specific structure and $ARGUMENTS placeholder

### 2. File Creation Process

```bash
# Create the command file
/cli-tool/components/commands/optimize-images.md
```

### 3. Content Structure

```markdown
# Image Optimizer

Optimize images in $ARGUMENTS for web performance and reduced file sizes.

## Task

I'll analyze and optimize images including:

1. Compress JPEG, PNG, and WebP files
2. Generate responsive image variants
3. Add proper alt text suggestions
4. Create optimized file structure

## Process

I'll follow these steps:

1. Scan directory for image files
2. Analyze current file sizes and formats
3. Apply compression algorithms
4. Generate multiple size variants
5. Create optimization report

## Optimization Types

### Compression
- Lossless compression for PNG files
- Quality optimization for JPEG files
- Modern WebP format conversion

### Responsive Images
- Generate multiple breakpoint sizes
- Create srcset attributes
- Optimize for different device densities

I'll adapt to your project's needs and follow performance best practices.
```

### 4. Installation Command Result

After creating the command, users can install it with:
```bash
npx claude-code-templates@latest --command="optimize-images" --yes
```

This will:
- Read from `cli-tool/components/commands/optimize-images.md`
- Copy the command to the user's `.claude/commands/` directory
- Enable the command for Claude Code usage

### 5. Usage in Claude Code

Users can then run the command in Claude Code:
```
/optimize-images src/assets/images
```

## Best Practices

- Create files in `cli-tool/components/commands/` directory
- Follow the Markdown format exactly as shown in examples
- Use $ARGUMENTS placeholder for user input
- Include comprehensive task descriptions and processes
- Test with the CLI installation command
- Provide actionable and specific outputs
- Document all parameters and options clearly

## Common Mistakes to Avoid

- ❌ Incorrect Markdown format
- ❌ Missing $ARGUMENTS placeholder
- ❌ Unclear task descriptions
- ❌ No error handling
- ❌ Missing validation steps
- ❌ Poor naming conventions

When creating CLI commands, always follow these standards and provide production-ready implementations that are robust, secure, and performant.

