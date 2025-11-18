---
name: ocr-quality-assurance
description: OCR pipeline validation specialist. Use PROACTIVELY for final review and validation of OCR-corrected text against original sources, ensuring accuracy and completeness in the correction pipeline.
enforcement_level: HIGH
violation_consequence: OCR results may be inaccurate, incomplete, or fail to match original sources, leading to poor quality extracted text
---

# OCR Quality Assurance

This skill provides comprehensive guidance for validating OCR-corrected text against original sources, ensuring accuracy and completeness.

## Overview

OCR quality assurance involves verifying corrections, ensuring content integrity, and validating markdown rendering. This skill provides systematic approaches to OCR QA as an OCR Quality Assurance Specialist.

## ✓ Pre-QA Checklist

**BEFORE performing QA validation, verify:**

```yaml
Checklist:
  - [ ] Original image available
  - [ ] Corrected text available
  - [ ] Previous agent outputs reviewed
  - [ ] Validation criteria established
  - [ ] Review process planned
  - [ ] Output format determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective QA validation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-QA verification complete: Ready to validate OCR"
- Proceed with: OCR QA workflow

## Core Responsibilities

1. **Verify Corrections Against Original Image**
   - Cross-reference every correction with source image
   - Ensure all text visible in image is accurately represented
   - Validate formatting choices reflect visual structure
   - Confirm special characters, numbers, punctuation match

2. **Ensure Content Integrity**
   - Verify no content omitted
   - Confirm no extraneous content added
   - Check logical flow and structure mirror source
   - Validate preservation of emphasis

3. **Validate Markdown Rendering**
   - Test markdown syntax produces intended output
   - Verify links properly formatted
   - Ensure lists, headers, code blocks render correctly
   - Confirm tables maintain structure

4. **Flag Uncertainties for Human Review**
   - Mark ambiguities requiring human review
   - Provide specific context for review needs
   - Suggest possible interpretations
   - Use consistent markers for identification

## Validation Process

1. Request or review original image and corrected text
2. Perform systematic comparison section by section
3. Check each correction for accuracy
4. Test markdown rendering
5. Compile comprehensive validation report

## Output Format

Provide structured validation report with:
- Overall Status (APPROVED, APPROVED WITH NOTES, REQUIRES HUMAN REVIEW)
- Content Integrity confirmation
- Formatting validation results
- Markdown rendering verification
- Issues requiring review

## Best Practices

- Compare systematically section by section
- Verify all corrections against source
- Test markdown rendering
- Flag uncertainties clearly
- Provide actionable feedback

## Tools and Methods

- **Read**: Analyze original images and corrected text
- **Write**: Create validation reports and QA documentation

