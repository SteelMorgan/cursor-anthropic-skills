---
name: llm-maintenance
description: This skill provides guidance for generating and maintaining LLMs.txt roadmap files for AI crawlers. This skill should be used after build completion, content changes, or when implementing AI Engine Optimization (AEO). Scans site structure and updates AI crawler navigation systematically.
enforcement_level: MEDIUM
violation_consequence: LLMs.txt file may be incomplete or incorrectly formatted, affecting AI crawler navigation
---

# LLM Maintenance

This skill provides systematic guidance for creating and maintaining LLMs.txt roadmap files that help AI crawlers understand site structure and content. It ensures consistent, accurate navigation information for AI systems.

## Overview

LLMs.txt files serve as roadmaps for AI crawlers, providing structured information about site pages, their purposes, and metadata. This skill provides a systematic approach to generating and maintaining these files.

## ✓ Pre-Action Verification

**BEFORE creating or updating llms.txt, verify:**

```yaml
Checklist:
  - [ ] Site root directory identified
  - [ ] Base URL determined or can be obtained
  - [ ] Content directories located (/app, /pages, /content, /docs, /blog)
  - [ ] Write permissions for public/llms.txt
  - [ ] Existing llms.txt reviewed (if present)

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for accurate llms.txt generation
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-action verification complete: Ready to generate llms.txt"
- Proceed with: LLMs.txt generation workflow

## Workflow

Follow this exact sequence every time when creating or updating llms.txt:

### Step 1: Identify Site Root & Base URL

- Look for `process.env.BASE_URL`, `NEXT_PUBLIC_SITE_URL`, or read "homepage" from package.json
- If none found, ask the user for the domain explicitly
- This will be the base URL for all page entries

**Output**: "✅ Base URL identified: [URL]"

### Step 2: Discover Candidate Pages

Recursively scan these directories:
- `/app` (Next.js App Router)
- `/pages` (Next.js Pages Router)
- `/content` (content directories)
- `/docs` (documentation)
- `/blog` (blog posts)

**IGNORE files matching these patterns:**
- Paths with `/_*` (private/internal routes)
- `/api/` routes
- `/admin/` or `/beta/` paths
- Files ending in `.test`, `.spec`, `.stories`
- Focus only on user-facing content pages

**Output**: "✅ Candidate pages discovered: [count] pages"

### Step 3: Extract Metadata for Each Page

Prioritize metadata sources in this order:

1. `export const metadata = { title, description }` (Next.js App Router)
2. `<Head><title>` & `<meta name="description">` (legacy pages)
3. Front-matter YAML in MD/MDX files
4. If none present, generate concise descriptions (≤120 chars) starting with action verbs like "Learn", "Explore", "See"

**Formatting rules:**
- Truncate titles to ≤70 chars
- Truncate descriptions to ≤120 chars
- Use action verbs in descriptions

**Output**: "✅ Metadata extracted for [count] pages"

### Step 4: Build LLMs.txt Skeleton

If the file doesn't exist, start with:

```
# ===== LLMs Roadmap =====
Site: {baseUrl}
Generated: {ISO-date-time}
User-agent: *
Allow: /
Train: no
Attribution: required
License: {baseUrl}/terms
```

**IMPORTANT**: Preserve any manual blocks bounded by `# BEGIN CUSTOM` ... `# END CUSTOM`

**Output**: "✅ LLMs.txt skeleton created"

### Step 5: Populate Page Entries

Organize by top-level folders (Docs, Blog, Marketing, etc.):

```
Section: Docs
Title: Quick-Start Guide
URL: /docs/getting-started
Desc: Learn to call the API in 5 minutes.

Title: API Reference
URL: /docs/api
Desc: Endpoint specs & rate limits.
```

**Output**: "✅ Page entries populated: [count] entries"

### Step 6: Detect Differences

- Compare new content with existing llms.txt
- If no changes needed, respond with "No update needed"
- If changes detected, overwrite `public/llms.txt` atomically

**Output**: "✅ Changes detected: [summary]" OR "ℹ️ Already current"

### Step 7: Optional Git Operations

If Git is available and appropriate:

```bash
git add public/llms.txt
git commit -m "chore(aeo): update llms.txt"
git push
```

**Output**: "✅ Git operations completed" (if executed)

### Step 8: Provide Clear Summary

Respond with:
- ✅ Updated llms.txt OR ℹ️ Already current
- Page count and sections affected
- Next steps if any errors occurred

## Safety Constraints

**NEVER**:
- ❌ Write outside `public/llms.txt`
- ❌ Expose secret environment variables in responses
- ❌ Delete existing entries without confirmation
- ❌ Ignore user's custom content blocks

**ALWAYS**:
- ✅ Preserve manual blocks (`# BEGIN CUSTOM` ... `# END CUSTOM`)
- ✅ Ask for confirmation before deleting entries
- ✅ Warn if >500 entries detected and ask for curation guidance
- ✅ Handle missing directories gracefully

## Error Handling

If errors occur:

1. **Base URL cannot be determined**:
   - Action: Ask user explicitly for domain
   - Do not proceed without base URL

2. **File permissions prevent writing**:
   - Action: Suggest alternative approaches
   - Check directory permissions
   - Verify file is not locked

3. **Metadata extraction fails for specific pages**:
   - Action: Generate reasonable defaults
   - Use filename or path as fallback
   - Document missing metadata

4. **Missing directories or empty content folders**:
   - Action: Handle gracefully
   - Skip empty directories
   - Report in summary

## Best Practices

- Run after build completion to capture latest structure
- Update after significant content changes
- Review generated file before committing
- Test with AI crawlers if possible
- Keep custom blocks for manual overrides
- Document any manual curation decisions

## Output Format

The generated llms.txt file should:

- Have clear section organization
- Include all user-facing pages
- Exclude internal/admin routes
- Provide concise, actionable descriptions
- Maintain consistent formatting
- Preserve custom content blocks

## Key Principles

1. **Systematic scanning**: Follow the exact sequence for consistency
2. **Metadata priority**: Use highest quality metadata source available
3. **User-facing focus**: Only include publicly accessible content
4. **Preservation**: Never lose user's custom content
5. **Atomic updates**: Overwrite file atomically to prevent corruption
6. **Clear communication**: Provide detailed summary of changes

