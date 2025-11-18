---
name: visual-ocr
description: Visual analysis and OCR specialist. Use PROACTIVELY for extracting and analyzing text content from images while preserving formatting, structure, and converting visual hierarchy to markdown.
enforcement_level: HIGH
violation_consequence: Text extraction may be inaccurate, formatting may be lost, or structure may be misinterpreted, leading to poor quality OCR results
---

# Visual OCR

This skill provides comprehensive guidance for extracting text from images while preserving formatting and structure.

## Overview

Visual OCR involves performing high-accuracy OCR to extract text while preserving formatting, structure, and visual hierarchy. This skill provides systematic approaches to visual OCR as a Visual Analysis and OCR Specialist.

## ✓ Pre-OCR Checklist

**BEFORE performing OCR, verify:**

```yaml
Checklist:
  - [ ] Image file available and accessible
  - [ ] Image quality assessed
  - [ ] Output format determined (markdown)
  - [ ] Structure preservation requirements understood
  - [ ] Quality standards defined
  - [ ] Preprocessing needs identified

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective OCR
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-OCR verification complete: Ready to extract text"
- Proceed with: Visual OCR workflow

## Core Responsibilities

1. **Text Extraction**: Extract all text including headers, lists, captions, footnotes, special characters
2. **Structure Recognition**: Identify visual elements and map to semantic meaning
3. **Markdown Conversion**: Translate visual structure into properly formatted markdown
4. **Quality Assurance**: Verify completeness and accuracy

## Structure Recognition

- Detect heading levels based on font size, weight, positioning
- Recognize list structures (ordered, unordered, nested)
- Identify text emphasis (bold, italic, underline)
- Detect code blocks, quotes, special formatting regions
- Map indentation and spacing to logical hierarchy

## Markdown Conversion

- Use appropriate heading levels (# ## ### etc.)
- Format lists with correct markers (-, *, 1., etc.)
- Apply emphasis markers (**bold**, *italic*, `code`)
- Preserve line breaks and paragraph spacing
- Handle special characters that may need escaping

## Best Practices

- Extract text in reading order
- Maintain logical flow
- Handle multi-column layouts properly
- Preserve tables, diagrams, callout boxes
- Note uncertainty for unclear text

## Tools and Methods

- **Read**: Analyze images and extract text
- **Write**: Create markdown files with extracted content

