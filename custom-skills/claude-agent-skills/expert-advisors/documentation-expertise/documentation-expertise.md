---
name: documentation-expertise
description: Use this skill to create, improve, and maintain project documentation. Specializes in technical writing, documentation standards, and generating documentation from code.
enforcement_level: HIGH
violation_consequence: Project documentation may be incomplete, outdated, or unclear, leading to poor developer experience and increased support burden
---

# Documentation Expertise

This skill provides comprehensive guidance for creating, improving, and maintaining clear, concise, and comprehensive documentation for software projects.

## Overview

Documentation expertise involves creating high-quality technical documentation that improves developer experience and project maintainability. This skill provides systematic approaches to documentation as a Documentation Expert specializing in technical writing and documentation standards.

## ✓ Pre-Documentation Checklist

**BEFORE creating or updating documentation, verify:**

```yaml
Checklist:
  - [ ] Target audience identified (developers, end-users, etc.)
  - [ ] Information to document gathered
  - [ ] Documentation structure planned
  - [ ] Code examples prepared
  - [ ] Existing documentation reviewed
  - [ ] Documentation standards understood

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective documentation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-documentation verification complete: Ready to create documentation"
- Proceed with: Documentation workflow

## Core Expertise Areas

- **Technical Writing**: Writing clear and easy-to-understand explanations of complex technical concepts
- **Documentation Standards**: Applying documentation standards and best practices, such as the "Diátaxis" framework or "Docs as Code"
- **API Documentation**: Generating and maintaining API documentation using standards like OpenAPI/Swagger
- **Code Documentation**: Writing meaningful code comments and generating documentation from them using tools like JSDoc, Sphinx, or Doxygen
- **User Guides and Tutorials**: Creating user-friendly guides and tutorials to help users get started with the project

## When to Use This Skill

Use this skill for:
- Creating or updating project documentation (e.g., README, CONTRIBUTING, USAGE)
- Writing documentation for new features or APIs
- Improving existing documentation for clarity and completeness
- Generating documentation from code comments
- Creating tutorials and user guides

## Documentation Process

1. **Understand the audience**: Identify the target audience for the documentation (e.g., developers, end-users)
2. **Gather information**: Collect all the necessary information about the feature or project to be documented
3. **Structure the documentation**: Organize the information in a logical and easy-to-follow structure
4. **Write the content**: Write the documentation in a clear, concise, and professional style
5. **Review and revise**: Review the documentation for accuracy, clarity, and completeness

## Documentation Checklist

- [ ] Is the documentation clear and easy to understand?
- [ ] Is the documentation accurate and up-to-date?
- [ ] Is the documentation complete?
- [ ] Is the documentation well-structured and easy to navigate?
- [ ] Is the documentation free of grammatical errors and typos?

## Output Format

Provide well-structured Markdown files with:
- **Clear headings and sections**
- **Code blocks with syntax highlighting**
- **Links to relevant resources**
- **Images and diagrams where appropriate**

## Documentation Standards

### Diátaxis Framework
- **Tutorials**: Learning-oriented, step-by-step guides
- **How-to Guides**: Problem-oriented, task-focused instructions
- **Reference**: Information-oriented, technical descriptions
- **Explanation**: Understanding-oriented, conceptual explanations

### Docs as Code
- Version control for documentation
- Code review for documentation changes
- Automated testing and validation
- Continuous integration for documentation

## Code Documentation Tools

### JSDoc (JavaScript)
```javascript
/**
 * Calculates the sum of two numbers
 * @param {number} a - First number
 * @param {number} b - Second number
 * @returns {number} Sum of a and b
 */
function add(a, b) {
  return a + b;
}
```

### Sphinx (Python)
```python
def calculate_sum(a: int, b: int) -> int:
    """
    Calculates the sum of two numbers.
    
    Args:
        a: First number
        b: Second number
    
    Returns:
        Sum of a and b
    """
    return a + b
```

### Doxygen (C/C++)
```cpp
/**
 * Calculates the sum of two numbers
 * @param a First number
 * @param b Second number
 * @return Sum of a and b
 */
int add(int a, int b);
```

## API Documentation Standards

### OpenAPI/Swagger
- Complete endpoint definitions
- Request/response schemas
- Authentication requirements
- Example requests and responses

### REST API Documentation
- Endpoint URLs and methods
- Request parameters and body
- Response formats and status codes
- Error handling and codes

## Best Practices

- Write for your audience's skill level
- Use active voice and clear language
- Include real examples and practical scenarios
- Test instructions by following them exactly
- Keep documentation up-to-date with code changes
- Use consistent formatting and structure
- Provide troubleshooting sections
- Include links to related resources

## Tools and Methods

- **Read**: Review code, existing documentation, and user feedback
- **Write/Edit**: Create documentation files, guides, and tutorials
- **Grep**: Search for code patterns, examples, and related content

## Common Documentation Types

### README Files
- Project description and purpose
- Installation and setup instructions
- Usage examples
- Contributing guidelines
- License information

### API Documentation
- Endpoint descriptions
- Request/response examples
- Authentication details
- Error handling

### User Guides
- Getting started tutorials
- Feature explanations
- Common use cases
- Troubleshooting

