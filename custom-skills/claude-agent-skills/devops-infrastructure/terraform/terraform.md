---
name: terraform
description: Terraform and Infrastructure as Code specialist. Use PROACTIVELY for Terraform modules, state management, IaC best practices, provider configurations, workspace management, and drift detection.
enforcement_level: HIGH
violation_consequence: Infrastructure may be poorly managed, state may be corrupted, or configurations may be non-reproducible, leading to deployment failures and infrastructure drift
---

# Terraform

This skill provides comprehensive guidance for Terraform and Infrastructure as Code automation and state management.

## Overview

Terraform involves infrastructure automation, state management, and Infrastructure as Code best practices. This skill provides systematic approaches to Terraform as a Terraform specialist focused on infrastructure automation.

## ✓ Pre-Terraform Checklist

**BEFORE using Terraform, verify:**

```yaml
Checklist:
  - [ ] Infrastructure requirements defined
  - [ ] Provider and version constraints determined
  - [ ] State management strategy planned
  - [ ] Module structure designed
  - [ ] Workspace strategy defined
  - [ ] CI/CD integration planned

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective Terraform usage
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-Terraform verification complete: Ready to use Terraform"
- Proceed with: Terraform workflow

## Focus Areas

- **Module design** with reusable components
- **Remote state management** (Azure Storage, S3, Terraform Cloud)
- **Provider configuration** and version constraints
- **Workspace strategies** for multi-environment
- **Import existing resources** and drift detection
- **CI/CD integration** for infrastructure changes

## Approach

1. DRY principle - create reusable modules
2. State files are sacred - always backup
3. Plan before apply - review all changes
4. Lock versions for reproducibility
5. Use data sources over hardcoded values

## Output Deliverables

- Terraform modules with input variables
- Backend configuration for remote state
- Provider requirements with version constraints
- Makefile/scripts for common operations
- Pre-commit hooks for validation
- Migration plan for existing infrastructure

## Best Practices

- Always include .tfvars examples
- Show both plan and apply outputs
- Use version constraints for providers
- Implement proper state management
- Create reusable modules
- Test configurations before applying

## Tools and Methods

- **Read**: Analyze existing infrastructure and configurations
- **Write/Edit**: Create Terraform modules and configurations
- **Bash**: Run terraform commands, validate configurations

