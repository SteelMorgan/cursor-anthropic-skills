---
name: social-media-clips
description: Social media video clip optimization specialist. Use PROACTIVELY for creating platform-specific clips with proper aspect ratios, subtitles, thumbnails, and encoding optimization.
enforcement_level: MEDIUM
violation_consequence: Social media clips may have incorrect aspect ratios, poor quality, or missing subtitles, leading to poor engagement and platform rejection
---

# Social Media Clips

This skill provides comprehensive guidance for creating platform-specific video clips optimized for social media platforms.

## Overview

Social media clip creation involves analyzing source content, creating platform-specific versions, and optimizing for engagement. This skill provides systematic approaches to social media clip creation as a Social Media Clip Optimization Specialist.

## ✓ Pre-Creation Checklist

**BEFORE creating social media clips, verify:**

```yaml
Checklist:
  - [ ] Source video available
  - [ ] Target platforms identified
  - [ ] Key moments identified
  - [ ] Aspect ratio requirements understood
  - [ ] Duration limits known
  - [ ] Encoding requirements determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective clip creation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-creation verification complete: Ready to create clips"
- Proceed with: Social media clip creation workflow

## Platform Specifications

- **TikTok/Instagram Reels**: 9:16 aspect ratio, 60 seconds maximum, H.264 video codec, AAC audio codec
- **YouTube Shorts**: 9:16 aspect ratio, 60 seconds maximum, H.264 video codec, AAC audio codec
- **Twitter**: 16:9 aspect ratio, 2 minutes 20 seconds maximum, H.264 video codec, AAC audio codec
- **LinkedIn**: 16:9 aspect ratio, 10 minutes maximum, H.264 video codec, AAC audio codec

## Core Responsibilities

- Analyze source video content to identify engaging segments
- Create platform-specific clips adhering to technical requirements
- Apply optimal encoding settings
- Generate and embed captions/subtitles
- Create eye-catching thumbnails
- Provide detailed metadata for each clip

## Quality Control Checklist

- Verify aspect ratios match platform requirements
- Ensure durations are within platform limits
- Confirm captions are properly synced and readable
- Check file sizes are optimized
- Validate thumbnails capture engaging moments
- Test that audio levels are normalized

## Best Practices

- Maintain focus on important visual elements
- Optimize encoding for quality and file size
- Ensure captions are readable and synced
- Extract thumbnails at compelling moments
- Generate comprehensive metadata

## Tools and Methods

- **Bash**: Execute FFmpeg commands for video processing
- **Read**: Analyze source video and requirements
- **Write**: Create clip configurations and metadata

