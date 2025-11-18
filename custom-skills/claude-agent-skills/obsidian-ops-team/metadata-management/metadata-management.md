---
name: metadata-management
description: This skill provides specialized guidance for managing frontmatter metadata in Obsidian vaults and knowledge management systems. This skill should be used when standardizing frontmatter, adding metadata to files, ensuring consistent file metadata across vaults, or maintaining metadata standards. Uses scripts for deterministic metadata operations.
enforcement_level: MEDIUM
violation_consequence: Metadata operations may be inconsistent or incomplete, requiring manual fixes
---

# Metadata Management

This skill provides comprehensive guidance for managing frontmatter metadata in Obsidian vaults and similar knowledge management systems. It ensures consistent metadata standards across all files and uses scripts for reliable, deterministic operations.

## Overview

Metadata management involves adding, standardizing, and maintaining frontmatter metadata in markdown files. This skill provides systematic approaches to metadata operations, ensuring consistency and reliability through script-based workflows.

## ✓ Pre-Action Verification

**BEFORE performing metadata operations, verify:**

```yaml
Checklist:
  - [ ] Vault path identified or current directory is vault root
  - [ ] Python 3.11+ is available
  - [ ] Script exists: scripts/metadata_adder.py (relative to skill directory)
  - [ ] File permissions allow read/write operations
  - [ ] Backup strategy considered (for production vaults)

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing prerequisites for safe metadata operations
- Next step: Fulfill missing prerequisites before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-action verification complete: Ready for metadata operations"
- Proceed with: Metadata workflow

## Available Scripts

This skill includes executable scripts for performing metadata operations:

### scripts/metadata_adder.py

Main script for adding standardized frontmatter metadata to markdown files that lack it.

**Purpose:**
- Adds frontmatter to markdown files missing metadata
- Extracts creation dates from filesystem metadata
- Generates tags based on directory structure
- Determines file types based on path and content
- Maintains consistency across vault

**Usage:**
```bash
# Preview mode (dry-run) - recommended first step
python3 scripts/metadata_adder.py --dry-run --vault /path/to/vault

# Execute metadata addition
python3 scripts/metadata_adder.py --vault /path/to/vault
```

**Parameters:**
- `--vault`: Path to Obsidian vault (default: /Users/cam/VAULT01)
- `--dry-run`: Preview changes without modifying files (recommended first)

**Output:**
- Lists files that would be updated (dry-run mode)
- Shows files actually updated (execution mode)
- Provides statistics: processed, updated, skipped, errors

## Workflow with Scripts

**IMPORTANT**: This skill uses scripts for metadata operations. Do NOT generate frontmatter metadata directly in code.

### To add metadata to files:

1. **Check prerequisites**:
   - Verify Python 3.11+ is available: `python3 --version`
   - Verify script exists: `scripts/metadata_adder.py` (relative to skill directory)
   - Check vault path is correct
   - Ensure file permissions allow read/write

2. **Run preview** (recommended):
   ```bash
   python3 scripts/metadata_adder.py --dry-run --vault /path/to/vault
   ```
   - Review output to see which files would be updated
   - Verify no unexpected files are included
   - Check that changes look correct

3. **Review output** and verify changes:
   - Check list of files that would be updated
   - Verify file types are correctly determined
   - Confirm tags match directory structure
   - Ensure no system files are included

4. **Execute script** (after review):
   ```bash
   python3 scripts/metadata_adder.py --vault /path/to/vault
   ```
   - Script will add frontmatter to files missing it
   - Preserves existing content
   - Updates modification dates

5. **Verify results**:
   - Check that frontmatter was added correctly
   - Verify tags and types are correct
   - Confirm no files were corrupted
   - Review statistics output

**DO NOT**:
- ❌ Generate frontmatter YAML directly in code
- ❌ Manually create metadata structures
- ❌ Skip script execution and create metadata manually
- ❌ Modify existing valid frontmatter unless fixing errors

**Path Notes**:
- Scripts are located in `scripts/` directory relative to this skill
- Always use relative paths: `scripts/metadata_adder.py`
- Do not use absolute paths or paths outside skill directory
- Adapt `--vault` parameter to your vault location

## Metadata Standards

Follow these standards for consistent metadata:

### Required Frontmatter Fields

All files must have frontmatter with:
- `tags`: Hierarchical tag structure (e.g., `ai/agents`, `business/client-work`)
- `type`: File type (note, reference, moc, daily-note, template, system)
- `created`: Creation date (YYYY-MM-DD format)
- `modified`: Last modification date (YYYY-MM-DD format)
- `status`: File status (active, archive, draft)

### Tag Structure

Tags should follow hierarchical structure:
- Technology tags: `ai/agents`, `ai/llm`, `langchain`
- Business tags: `business/client-work`, `business/strategy`
- Content tags: `research`, `tutorial`, `idea`
- Temporal tags: `daily/YYYY/MM` for daily notes

### File Types

Supported file types:
- `note`: Standard note
- `reference`: Reference material
- `moc`: Map of Content
- `daily-note`: Daily note entry
- `template`: Template file
- `system`: System file

### Status Values

File status options:
- `active`: Currently active file
- `archive`: Archived file
- `draft`: Draft or work in progress

## Core Responsibilities

This skill provides guidance for:

1. **Add Standardized Frontmatter**: Add frontmatter to any markdown files missing it
   - Use script: `scripts/metadata_adder.py`
   - Always run with `--dry-run` first
   - Review changes before execution

2. **Extract Creation Dates**: Get creation dates from filesystem metadata
   - Script automatically extracts from filesystem
   - Falls back to current date if unavailable
   - Preserves existing dates in frontmatter

3. **Generate Tags**: Create tags based on directory structure and content
   - Script analyzes file path
   - Maps directories to tag hierarchy
   - Adds date tags for daily notes

4. **Determine File Types**: Assign appropriate type based on path and content
   - Script analyzes path patterns
   - Determines type automatically
   - Can be overridden manually if needed

5. **Maintain Consistency**: Ensure all metadata follows vault standards
   - Use script for bulk operations
   - Verify standards compliance
   - Update standards documentation as needed

## Important Notes

- **Never modify existing valid frontmatter** unless fixing errors
- **Preserve any existing metadata** when adding missing fields
- **Use filesystem dates** as fallback for creation/modification times
- **Tag generation** should reflect the file's location and content
- **Always test with `--dry-run`** before making changes
- **Backup vault** before bulk operations on production systems

## Error Handling

If script execution fails:

1. **Check Python version**: Requires Python 3.11+
2. **Verify vault path**: Ensure path is correct and accessible
3. **Check file permissions**: Ensure read/write access
4. **Review error messages**: Script provides specific error information
5. **Check file encoding**: Script expects UTF-8 encoded files

## Best Practices

- Always run `--dry-run` first to preview changes
- Review output carefully before executing
- Backup vault before bulk operations
- Test on small subset before full vault
- Document custom tag mappings if needed
- Keep metadata standards document updated

