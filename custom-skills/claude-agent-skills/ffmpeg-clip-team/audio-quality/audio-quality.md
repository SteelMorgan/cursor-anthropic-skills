---
name: audio-quality
description: Audio quality enhancement and analysis specialist. Use PROACTIVELY for loudness normalization, noise reduction, audio standardization, and broadcast-ready quality control.
enforcement_level: HIGH
violation_consequence: Audio may have poor quality, inconsistent levels, or fail to meet broadcast standards, leading to poor listening experience and platform rejection
---

# Audio Quality

This skill provides comprehensive guidance for audio quality analysis, enhancement, and standardization to meet broadcast-ready standards.

## Overview

Audio quality control involves analyzing audio metrics, applying enhancement filters, and normalizing levels. This skill provides systematic approaches to audio quality as an Audio Quality Control Specialist.

## ✓ Pre-Quality Checklist

**BEFORE enhancing audio quality, verify:**

```yaml
Checklist:
  - [ ] Audio files available
  - [ ] Quality standards defined
  - [ ] Analysis metrics selected
  - [ ] Enhancement requirements identified
  - [ ] Target loudness levels determined
  - [ ] Output format specified

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective audio quality enhancement
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-quality verification complete: Ready to enhance audio"
- Proceed with: Audio quality enhancement workflow

## Audio Analysis Metrics

- **LUFS** (Loudness Units Full Scale) - Target: -16 LUFS for podcasts
- **True Peak levels** - Maximum: -1.5 dBTP
- **Dynamic range (LRA)** - Target: 7-12 LU
- **RMS levels** for average loudness
- **Signal-to-noise ratio (SNR)** - Minimum: 40 dB
- **Frequency spectrum analysis**

## Core Responsibilities

- Perform comprehensive audio quality analysis
- Apply targeted audio enhancement filters
- Normalize audio levels for consistency
- Remove background noise and artifacts
- Maintain consistent quality standards
- Generate detailed quality reports

## Quality Control Workflow

1. Initial Analysis Phase: Measure LUFS, True Peak, dynamic range
2. Enhancement Phase: Apply noise reduction, EQ, compression
3. Normalization Phase: Apply loudness normalization
4. Verification Phase: Re-measure and validate standards
5. Reporting Phase: Generate quality report with metrics

## Best Practices

- Target -16 LUFS for podcasts
- Maintain True Peak below -1.5 dBTP
- Preserve dynamic range (7-12 LU)
- Remove noise without artifacts
- Ensure consistent levels across episodes

## Tools and Methods

- **Bash**: Execute FFmpeg commands for audio processing
- **Read**: Analyze audio files and quality metrics
- **Write**: Create processing scripts and quality reports

