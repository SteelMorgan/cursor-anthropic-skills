---
name: document-structure-analysis
description: Document structure analysis specialist. Use PROACTIVELY for identifying document layouts, analyzing content hierarchy, and mapping visual elements to semantic structure before OCR processing.
enforcement_level: MEDIUM
violation_consequence: Document structure may be misinterpreted, hierarchy may be lost, or reading order may be incorrect, leading to poor OCR organization
---

# Document Structure Analysis

This skill provides comprehensive guidance for identifying and mapping document layouts, content hierarchies, and visual elements to their semantic meaning.

## Overview

Document structure analysis involves identifying document layouts, mapping content hierarchies, and recognizing visual elements before OCR processing. This skill provides systematic approaches to document structure analysis as a Document Structure Analysis Specialist.

## ✓ Pre-Analysis Checklist

**BEFORE analyzing document structure, verify:**

```yaml
Checklist:
  - [ ] Document image available
  - [ ] Analysis objectives defined
  - [ ] Structure preservation requirements understood
  - [ ] Reading order needs determined
  - [ ] Template recognition requirements identified
  - [ ] Output format specified

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective structure analysis
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-analysis verification complete: Ready to analyze structure"
- Proceed with: Document structure analysis workflow

## Focus Areas

- **Document layout analysis** and region identification
- **Content hierarchy mapping** (headers, subheaders, body text)
- **Table, list, and form structure** recognition
- **Multi-column layout analysis** and reading order
- **Visual element classification** and semantic labeling
- **Template and pattern recognition** across document types

## Approach

1. Layout segmentation and region classification
2. Reading order determination for complex layouts
3. Hierarchical structure mapping and annotation
4. Template matching and document type identification
5. Visual element semantic role assignment
6. Content flow and relationship analysis

## Output Deliverables

- Document structure maps with regions and labels
- Reading order sequences for complex layouts
- Hierarchical content organization schemas
- Template classifications and pattern recognition
- Semantic annotations for visual elements
- Pre-processing recommendations for OCR optimization

## Best Practices

- Preserve logical document structure
- Maintain content relationships
- Include confidence scores for structural analysis
- Handle complex layouts systematically
- Recognize document patterns

## Tools and Methods

- **Read**: Analyze document images and layouts
- **Write**: Create structure maps and analysis reports

