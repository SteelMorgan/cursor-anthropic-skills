---
name: enhanced-skill-creator
description: Guide for creating bulletproof skills with built-in enforcement. This skill combines Anthropic's Skill Creator methodology with 6 enforcement strategies to create skills that agents reliably execute. Use when creating or updating skills that require strong compliance guarantees.
license: Based on Anthropic Skill Creator + custom enforcement techniques
---

# Enhanced Skill Creator: Building Bulletproof Skills

This skill provides comprehensive guidance for creating effective skills with built-in enforcement mechanisms that ensure reliable agent execution.

## About Skills

Skills are modular, self-contained packages that extend Claude's capabilities by providing specialized knowledge, workflows, and tools. Think of them as "onboarding guides" for specific domains or tasks—they transform Claude from a general-purpose agent into a specialized agent equipped with procedural knowledge that no model can fully possess.

### What Skills Provide

1. **Specialized workflows** - Multi-step procedures for specific domains
2. **Tool integrations** - Instructions for working with specific file formats or APIs
3. **Domain expertise** - Company-specific knowledge, schemas, business logic
4. **Bundled resources** - Scripts, references, and assets for complex and repetitive tasks
5. **Enforcement mechanisms** - Built-in compliance guarantees for critical workflows

### Anatomy of a Skill

Every skill consists of a required SKILL.md file and optional bundled resources:

```
skill-name/
├── SKILL.md (required)
│   ├── YAML frontmatter metadata (required)
│   │   ├── name: (required)
│   │   ├── description: (required)
│   │   ├── enforcement_level: (optional - CRITICAL|HIGH|MEDIUM|LOW)
│   │   └── violation_consequence: (optional - describes what happens on violation)
│   └── Markdown instructions (required)
└── Bundled Resources (optional)
    ├── scripts/          - Executable code (Python/Bash/etc.)
    ├── references/       - Documentation intended to be loaded into context as needed
    └── assets/           - Files used in output (templates, icons, fonts, etc.)
```

#### SKILL.md (required)

**Metadata Quality:** The `name` and `description` in YAML frontmatter determine when Claude will use the skill. Be specific about what the skill does and when to use it. Use the third-person (e.g. "This skill should be used when..." instead of "Use this skill when...").

**Enhanced Frontmatter:** For skills requiring strict compliance, add:
- `enforcement_level: CRITICAL|HIGH|MEDIUM|LOW` - Indicates how strictly the skill must be followed
- `violation_consequence: <description>` - Explains what happens if the skill is violated

#### Bundled Resources (optional)

##### Scripts (`scripts/`)

Executable code (Python/Bash/etc.) for tasks that require deterministic reliability or are repeatedly rewritten.

- **When to include**: When the same code is being rewritten repeatedly or deterministic reliability is needed
- **Example**: `scripts/rotate_pdf.py` for PDF rotation tasks
- **Benefits**: Token efficient, deterministic, may be executed without loading into context
- **Note**: Scripts may still need to be read by Claude for patching or environment-specific adjustments

##### References (`references/`)

Documentation and reference material intended to be loaded as needed into context to inform Claude's process and thinking.

- **When to include**: For documentation that Claude should reference while working
- **Examples**: `references/finance.md` for financial schemas, `references/api_docs.md` for API specifications, `references/routing-table.md` for conditional routing rules
- **Use cases**: Database schemas, API documentation, domain knowledge, company policies, detailed workflow guides, enforcement routing tables
- **Benefits**: Keeps SKILL.md lean, loaded only when Claude determines it's needed
- **Best practice**: If files are large (>10k words), include grep search patterns in SKILL.md
- **Avoid duplication**: Information should live in either SKILL.md or references files, not both

##### Assets (`assets/`)

Files not intended to be loaded into context, but rather used within the output Claude produces.

- **When to include**: When the skill needs files that will be used in the final output
- **Examples**: `assets/logo.png` for brand assets, `assets/slides.pptx` for PowerPoint templates
- **Use cases**: Templates, images, icons, boilerplate code, fonts, sample documents that get copied or modified
- **Benefits**: Separates output resources from documentation, enables Claude to use files without loading them into context

### Progressive Disclosure Design Principle

Skills use a three-level loading system to manage context efficiently:

1. **Metadata (name + description)** - Always in context (~100 words)
2. **SKILL.md body** - When skill triggers (<5k words)
3. **Bundled resources** - As needed by Claude (Unlimited*)

*Unlimited because scripts can be executed without reading into context window.

---

## Enforcement-First Design

For skills that require strict compliance (e.g., security-critical operations, data validation, API interactions), incorporate enforcement mechanisms to ensure agents reliably follow the skill's instructions.

### The 6 Enforcement Strategies

#### Strategy 1: First-Line Blocker ⛔

**When to use**: Critical skills where execution must be blocked until prerequisites are met.

**Purpose**: Create an immediate visual and procedural barrier that prevents the agent from proceeding without explicit action.

**Template**:

```markdown
# ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT READ FURTHER UNTIL YOU EXECUTE THIS:**

```python
# MANDATORY - Execute immediately:
read_file("path/to/required/file.md")
```

**DID YOU EXECUTE? Yes / No**

IF NO → STOP READING, EXECUTE NOW
IF YES → Output: "✅ [File name] loaded" and continue

---

[Rest of skill content here]
```

**Why it works**:
- Visual blocker (⛔⛔⛔) captures attention
- Requires explicit action BEFORE proceeding
- Executable code block for immediate use
- Yes/No question creates mental checkpoint

**Example use cases**:
- Skills requiring external validation (API checks, database queries)
- Skills with mandatory prerequisites (config files, authentication)
- Security-critical workflows

---

#### Strategy 2: Checkpoint-Based Gates 🔒

**When to use**: Complex multi-step workflows where each step must be verified before proceeding.

**Purpose**: Break the workflow into explicit gates with mandatory confirmations at each stage.

**Template**:

```markdown
## 🔒 Gate System

### Gate 1: [Step Name] ✋ STOP HERE FIRST
- **Action**: [Specific action required]
- **Confirmation**: Output "Gate 1 cleared: [brief description]"

### Gate 2: [Step Name] ✋ STOP HERE SECOND
- **Action**: [Specific action required]
- **Confirmation**: Output "Gate 2 cleared: [brief description]"

### Gate 3: [Step Name] ✋ STOP HERE THIRD
- **Action**: [Specific action required]
- **Confirmation**: Output "Gate 3 cleared: [brief description]"

## 🚦 Final Checkpoint

**Before proceeding, verify:**
```
✅ ALL GATES CLEARED
- Gate 1: [status]
- Gate 2: [status]
- Gate 3: [status]

Ready to proceed: [YES/NO]
```

**IF ANY GATE NOT CLEARED → STOP and complete missing gate**
```

**Why it works**:
- Visual checkpoints create clear structure
- Each gate requires explicit confirmation
- Intermediate outputs create audit trail
- Easy to debug which step failed

**Example use cases**:
- Data validation pipelines
- Multi-stage code generation
- API integration workflows

---

#### Strategy 3: Self-Verification Checklists ✓

**When to use**: Skills where agents must verify multiple conditions before proceeding.

**Purpose**: Provide explicit checklist that agent must mentally (or explicitly) verify.

**Template**:

```markdown
## Pre-Action Verification

**BEFORE proceeding with [action], verify:**

```yaml
Checklist:
  - [ ] [Condition 1 verified]
  - [ ] [Condition 2 verified]
  - [ ] [Condition 3 verified]
  - [ ] [Condition 4 verified]

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: "[Missing condition]"
- Next step: "[How to fulfill condition]"

**IF ALL CHECKED:**
- Output: "✅ Pre-action verification complete"
- Proceed with: [action]
```

**Why it works**:
- Structured checklist format is clear
- YAML format is machine-readable
- Explicit STOP condition
- Provides remediation guidance

**Example use cases**:
- Code deployment checks
- File operation prerequisites
- Environment validation

---

#### Strategy 4: Conditional Routing Tables 🗺️

**When to use**: Skills with multiple entry points based on keywords or conditions.

**Purpose**: Provide explicit routing rules that map inputs to required actions.

**Template**:

```markdown
## Routing Rules

### IF keywords detected: [keyword1, keyword2, keyword3]

**MANDATORY SEQUENCE:**
```python
1. read_file("[required_file_1.md]")
2. [Validation action]
3. [Configuration action]
4. ONLY THEN proceed with [main task]
```

**Output**: "✅ Route [name] activated: [keywords detected]"

### IF keywords detected: [keyword4, keyword5]

**MANDATORY SEQUENCE:**
```python
1. read_file("[required_file_2.md]")
2. [Different validation]
3. ONLY THEN proceed with [alternative task]
```

**Output**: "✅ Route [name] activated: [keywords detected]"

---

## Violation Handling

**IF agent skips any step in sequence:**
```
❌ ERROR: Protocol violation detected
- Step skipped: [number and description]
- Required action: [specific action to take]
- Status: BLOCKED - cannot proceed until completed
```
```

**Why it works**:
- Keyword-based routing is explicit
- Mandatory sequences prevent shortcuts
- Violation handling is built-in
- Easy to extend with new routes

**Example use cases**:
- Multi-technology skills (handles Python vs JavaScript vs Bash)
- Context-dependent workflows
- Skills with multiple modes

---

#### Strategy 5: Machine-Readable YAML Configuration 📋

**When to use**: Complex skills where structured configuration improves reliability.

**Purpose**: Provide machine-readable configuration that LLMs parse more reliably than prose.

**Template**:

```markdown
## Skill Configuration

```yaml
skill_config:
  mode: strict  # strict | permissive
  
  mandatory_sequence:
    - step: 1
      action: read_file
      path: "[file_path]"
      confirmation: "✅ [Step 1] complete"
      
    - step: 2
      action: [action_type]
      parameters:
        param1: value1
        param2: value2
      confirmation: "✅ [Step 2] complete"
  
  enforcement:
    violation_action: STOP
    output_confirmation: true
    mention_sources: MANDATORY
  
  validation:
    type: checklist
    report_format: "✅ [Skill name] validation complete"
```

**To execute this skill:**
1. Parse the `mandatory_sequence` array
2. Execute each step in order
3. Output confirmation after each step
4. Follow enforcement rules strictly
```

**Why it works**:
- Structured format reduces ambiguity
- LLMs parse YAML reliably
- Easy to extend/modify
- Supports complex configurations

**Example use cases**:
- Skills with complex dependencies
- Multi-tool integrations
- Configurable workflows

---

#### Strategy 6: Consequence Declaration 🚨

**When to use**: All critical skills to establish clear expectations.

**Purpose**: Explicitly state what happens when skill rules are violated.

**Template**:

```markdown
## Enforcement & Consequences

```yaml
ENFORCEMENT_LEVEL: [CRITICAL|HIGH|MEDIUM|LOW]
VIOLATION_CONSEQUENCE: [Description of what happens]
SCOPE: [When enforcement applies]
```

**Compliance Requirements:**
- [ ] Requirement 1 - MANDATORY
- [ ] Requirement 2 - MANDATORY
- [ ] Requirement 3 - MANDATORY

**Consequences of Violation:**

IF agent violates requirements:
- ❌ Response is considered INVALID
- ❌ Generated code is REJECTED
- ❌ User will request restart with proper compliance
- ❌ [Other specific consequences]

**COMPLIANCE IS NOT OPTIONAL**
```

**Why it works**:
- Clear expectations from the start
- Consequences create accountability
- Visual markers (❌) emphasize seriousness
- YAML makes enforcement level explicit

**Example use cases**:
- All critical skills
- Security-sensitive operations
- Data integrity requirements

---

## Enhanced Skill Creation Process

Follow this 6-step process to create bulletproof skills with built-in enforcement.

### Step 1: Understanding the Skill with Concrete Examples

**Original step**: Gather concrete examples of how the skill will be used.

**Enhancement**: Also identify compliance requirements and potential failure modes.

**Questions to ask**:
- What functionality should this skill support?
- Can you give examples of how this skill would be used?
- What would a user say that should trigger this skill?
- **NEW**: What are the critical steps that must not be skipped?
- **NEW**: What happens if the agent violates this skill's rules?
- **NEW**: Are there security, data integrity, or safety concerns?

**Output**: 
- 3-5 concrete use cases
- List of critical compliance requirements
- Identified failure modes and their consequences

**Example**:
```
Skill: 1C BSL Code Generator
Use cases:
  1. "Create a справочник for customers"
  2. "Add validation to документ"
  3. "Generate query for регистр"

Critical requirements:
  - MUST validate metadata via MCP before generating
  - MUST NOT hallucinate API methods
  - MUST follow DSSL coding standards

Failure modes:
  - Hallucinated methods → compilation errors
  - Skipped validation → incorrect structure
  - Wrong standards → technical debt
```

---

### Step 2: Planning Reusable Contents

**Original step**: Identify scripts, references, and assets needed.

**Enhancement**: Also identify which steps require enforcement mechanisms.

**Analysis questions**:
1. What code is rewritten repeatedly? → Add to `scripts/`
2. What documentation is referenced often? → Add to `references/`
3. What templates/assets are reused? → Add to `assets/`
4. **NEW**: Which steps are critical and error-prone? → Needs enforcement
5. **NEW**: What routing rules exist? → Create `references/routing-table.md`
6. **NEW**: What validations are required? → Add to checklist

**Output**:
- List of scripts to create
- List of reference docs to include
- List of assets to bundle
- **NEW**: Enforcement strategy selection (which of 1-6 to use)
- **NEW**: Critical checkpoints identified

**Example**:
```
Skill: PDF Editor

Reusable contents:
  - scripts/rotate_pdf.py
  - scripts/merge_pdfs.py
  - references/pdf_operations.md

Enforcement needs:
  - Strategy 3 (Checklist): Verify file exists before processing
  - Strategy 6 (Consequences): Declare what happens on invalid PDF
  
Critical checkpoints:
  - Gate 1: Validate PDF file format
  - Gate 2: Check file permissions
  - Gate 3: Verify output path writable
```

---

### Step 3: Initializing the Skill

**Original step**: Run `init_skill.py` to create template structure.

**Enhancement**: Add enforcement fields to YAML frontmatter from the start.

**Enhanced YAML frontmatter template**:

```yaml
---
name: skill-name
description: [Third-person description of what skill does and when to use it]
enforcement_level: [CRITICAL|HIGH|MEDIUM|LOW]
violation_consequence: [What happens if skill is violated]
license: [License information]
---
```

**Enforcement level guide**:
- **CRITICAL**: Security, data integrity, legal compliance (use strategies 1,2,3,5,6)
- **HIGH**: Complex workflows, API integrations (use strategies 2,3,4,6)
- **MEDIUM**: Multi-step processes (use strategies 3,4)
- **LOW**: Simple linear tasks (use strategy 3 only)

**Usage**:

```bash
scripts/init_skill.py <skill-name> --path <output-directory>
```

Then immediately edit SKILL.md to add enforcement fields to frontmatter.

---

### Step 4: Edit the Skill

**Original step**: Write SKILL.md with procedural knowledge.

**Enhancement**: Incorporate selected enforcement strategies into the skill.

#### Writing Style (Enhanced)

**Base style** (from Skill Creator):
- Use imperative/infinitive form (verb-first instructions)
- Objective, instructional language
- "To accomplish X, do Y" not "You should do X"

**Enforcement style additions**:
- Use visual markers: ⛔ for STOP, 🚨 for warnings, ✅ for confirmations, ❌ for violations
- Write enforcement blocks in IMPERATIVE language: "MUST", "EXECUTE NOW", "STOP"
- Structure consequences as bullet lists with ❌ prefix
- Format confirmations consistently: "✅ [Action] complete"

#### Applying Enforcement Strategies

Based on enforcement_level identified in Step 3:

**If CRITICAL** (strategies 1,2,3,5,6):
```markdown
# ⛔⛔⛔ STOP ⛔⛔⛔
[First-line blocker from Strategy 1]

---

## 🔒 Workflow Gates
[Gate system from Strategy 2]

---

## ✓ Pre-Action Verification
[Checklist from Strategy 3]

---

## 📋 Configuration
[YAML config from Strategy 5]

---

## 🚨 Enforcement & Consequences
[Consequences from Strategy 6]

---

[Rest of skill content]
```

**If HIGH** (strategies 2,3,4,6):
```markdown
## 🔒 Workflow Gates
[Gate system]

## ✓ Verification
[Checklist]

## 🗺️ Routing Rules
[Routing table]

## 🚨 Consequences
[Violations]

[Rest of skill content]
```

**If MEDIUM** (strategies 3,4):
```markdown
## ✓ Pre-Action Checklist
[Checklist]

## 🗺️ Routing
[If applicable]

[Rest of skill content]
```

**If LOW** (strategy 3 only):
```markdown
## Quick Verification
- [ ] [Basic check 1]
- [ ] [Basic check 2]

[Rest of skill content]
```

#### Content Organization

1. **Frontmatter** - Include enforcement_level
2. **Introduction** - What skill does
3. **Enforcement blocks** - Based on level (strategies 1-6)
4. **Core instructions** - How to use the skill
5. **Resource references** - How to use scripts/references/assets
6. **Examples** - Concrete usage examples

#### Delete Example Files

Remove any example files from initialization that aren't needed for this specific skill.

---

### Step 5: Packaging a Skill

**Original step**: Run `package_skill.py` to validate and create distributable zip.

**Enhancement**: Validation now includes enforcement checks.

```bash
scripts/package_skill.py <path/to/skill-folder>
```

**Enhanced validation checks**:

1. **Standard checks** (from Skill Creator):
   - YAML frontmatter format and required fields
   - Skill naming conventions and directory structure
   - Description completeness and quality
   - File organization and resource references

2. **NEW - Enforcement checks**:
   - If enforcement_level is CRITICAL or HIGH:
     - ✓ Has at least one enforcement strategy implemented
     - ✓ Has violation_consequence declared
     - ✓ Has explicit confirmations/checkpoints
     - ✓ Uses consistent visual markers
   - For all levels:
     - ✓ enforcement_level matches actual enforcement implementation
     - ✓ Consequences are clearly stated if mandatory actions exist

**Manual enforcement verification**:

After packaging, test the skill by:
1. Using it in a conversation
2. Intentionally skipping a mandatory step
3. Verifying that enforcement mechanisms activate (STOP messages, violation warnings)
4. Confirming agent complies with gates/checklists

---

### Step 6: Iterate

**Original step**: Improve skill based on real usage feedback.

**Enhancement**: Also test and refine enforcement effectiveness.

**Iteration workflow**:
1. Use the skill on real tasks
2. Notice struggles or inefficiencies
3. Identify how SKILL.md or bundled resources should be updated
4. Implement changes and test again
5. **NEW**: Test enforcement compliance:
   - Does agent follow mandatory sequences?
   - Do checkpoints catch violations?
   - Are consequences clear when violations occur?
6. **NEW**: Adjust enforcement level if needed:
   - Too strict? → Reduce from CRITICAL to HIGH
   - Too lenient? → Add more enforcement strategies

**Enforcement iteration questions**:
- Did the agent skip any mandatory steps?
- Were violation messages clear and actionable?
- Did checkpoints add value or just overhead?
- Should enforcement level be adjusted?

---

## Enforcement Decision Matrix

Use this matrix to select appropriate enforcement strategies based on skill characteristics:

| Skill Characteristic | Recommended Strategies | Enforcement Level | Reasoning |
|---------------------|----------------------|------------------|-----------|
| **Security-critical** (auth, permissions, data access) | 1, 2, 3, 5, 6 | CRITICAL | Maximum enforcement required; cannot tolerate violations |
| **Data integrity** (database operations, file writes) | 2, 3, 5, 6 | CRITICAL | Must validate before actions; consequences severe |
| **API integrations** (external services, rate limits) | 2, 3, 4, 6 | HIGH | Multi-step validation; routing for different APIs |
| **Complex workflows** (5+ steps, branching logic) | 2, 4, 5 | HIGH | Gates prevent skipping steps; routing handles branches |
| **Code generation** (BSL, Python, etc.) | 2, 3, 4, 6 | HIGH | Validation critical; routing for different languages |
| **Multi-tool skills** (Docker + K8s + networking) | 3, 4, 5 | MEDIUM | Checklists for prerequisites; routing for tool selection |
| **Document creation** (DOCX, PDF, XLSX) | 3, 6 | MEDIUM | Basic validation; clear consequences for invalid templates |
| **Simple utilities** (file operations, text processing) | 3 | LOW | Basic checklist sufficient |
| **Read-only analysis** (log analysis, code review) | 3 | LOW | Minimal enforcement needed |

### Strategy Combination Guide

**Maximum enforcement** (CRITICAL skills):
```
Strategy 1 (First-line blocker)
  ↓
Strategy 2 (Gates) for each major step
  ↓
Strategy 3 (Checklist) before critical actions
  ↓
Strategy 5 (YAML config) for complex parameters
  ↓
Strategy 6 (Consequences) declared upfront
```

**Standard enforcement** (HIGH skills):
```
Strategy 2 (Gates) for workflow
  ↓
Strategy 4 (Routing) for different paths
  ↓
Strategy 3 (Checklist) before actions
  ↓
Strategy 6 (Consequences) declared
```

**Light enforcement** (MEDIUM skills):
```
Strategy 3 (Checklist) for prerequisites
  ↓
Strategy 4 (Routing) if multi-path
```

**Minimal enforcement** (LOW skills):
```
Strategy 3 (Basic checklist) only
```

---

## Examples of Bulletproof Skills

### Example 1: Critical Skill (1C BSL Code Generator)

**Enforcement strategies used**: 1, 2, 3, 5, 6

```yaml
---
name: 1c-bsl-generator
description: Generate 1C BSL code with validation via MCP. This skill MUST validate all metadata and API calls before code generation to prevent hallucinations. Use when creating 1C справочники, документы, or регистры.
enforcement_level: CRITICAL
violation_consequence: Generated code will fail compilation or cause runtime errors. Hallucinated API methods are not acceptable.
---
```

```markdown
# ⛔⛔⛔ STOP ⛔⛔⛔

**DO NOT GENERATE ANY 1C CODE UNTIL YOU:**

```python
# MANDATORY validations:
read_file("D:\\My Projects\\FrameWork Global\\LLM Skills\\custom-skills\\1C_BSL_SKILL.md")
# Then use MCP to validate metadata:
# mcp_1c-metacode_search_metadata("[object_name]")
# mcp_bsl-platform-context_search("[api_method]", "method")
```

**DID YOU COMPLETE VALIDATIONS? Yes / No**

IF NO → STOP, validate first
IF YES → Output: "✅ 1C metadata validated" and continue

---

## 🔒 Code Generation Gates

### Gate 1: Metadata Validation ✋
- Action: Search existing metadata via `mcp_1c-metacode_search_metadata`
- Verify: Object doesn't already exist or get existing structure
- Confirmation: "Gate 1 cleared: Metadata validated"

### Gate 2: API Verification ✋
- Action: Validate ALL methods via `mcp_bsl-platform-context_search`
- Verify: No hallucinated API calls
- Confirmation: "Gate 2 cleared: API methods verified"

### Gate 3: Standards Check ✋
- Action: Confirm DSSL standards compliance
- Verify: Naming, structure, comments follow standards
- Confirmation: "Gate 3 cleared: Standards verified"

## 🚨 CRITICAL - Violation Consequences

```yaml
ENFORCEMENT_LEVEL: CRITICAL
VIOLATION_CONSEQUENCE: CODE_REJECTED
```

**IF you generate code without validation:**
- ❌ Code is INVALID and will be rejected
- ❌ Compilation errors likely
- ❌ User must restart with proper validation
- ❌ This is considered a critical failure

**ANTI-HALLUCINATION RULE:**
NEVER generate 1C code without MCP validation. Period.

[Rest of skill content...]
```

---

### Example 2: Medium Skill (PowerShell Script Generator)

**Enforcement strategies used**: 3, 4

```yaml
---
name: powershell-generator
description: Generate PowerShell scripts for Windows automation. This skill validates prerequisites and routes based on script complexity. Use when creating .ps1 scripts for file operations, system administration, or automation tasks.
enforcement_level: MEDIUM
violation_consequence: Scripts may fail execution or require manual fixes
---
```

```markdown
# PowerShell Script Generator

## 🗺️ Routing Rules

### IF keywords: [file, copy, move, delete, directory]
**Route**: File operations workflow
```python
1. Verify: Test-Path cmdlet availability
2. Add: Error handling with Try/Catch
3. Include: -ErrorAction parameter
4. THEN: Generate file operation script
```

### IF keywords: [service, process, registry, system]
**Route**: System administration workflow
```python
1. Verify: Administrator privileges required
2. Add: #Requires -RunAsAdministrator
3. Include: Detailed logging
4. THEN: Generate system admin script
```

### IF keywords: [network, web, download, http]
**Route**: Network operations workflow
```python
1. Verify: Invoke-WebRequest availability
2. Add: Timeout handling
3. Include: TLS 1.2 settings
4. THEN: Generate network script
```

## ✓ Pre-Generation Checklist

```yaml
Before generating script:
  - [ ] Target OS is Windows
  - [ ] PowerShell version determined (5.1 or 7+)
  - [ ] Required modules identified
  - [ ] Error handling strategy selected
  - [ ] Execution policy consideration included

Status: [READY / BLOCKED]
```

**IF checklist incomplete:**
- Ask user for missing information
- Do not proceed with assumptions

[Rest of skill content...]
```

---

### Example 3: Low Skill (Mermaid Diagram Creator)

**Enforcement strategies used**: 3

```yaml
---
name: mermaid-diagrams
description: Create Mermaid diagrams for architecture, flows, and relationships. This skill uses conservative syntax to ensure broad compatibility. Use when visualizing processes, system architecture, or data flows.
enforcement_level: LOW
violation_consequence: Diagram may fail to render or display incorrectly
---
```

```markdown
# Mermaid Diagram Creator

## Quick Verification

Before creating diagram:
- [ ] Diagram type identified (flowchart/sequence/class/er)
- [ ] Complexity assessed (simple/medium/complex)
- [ ] Special characters checked (avoid in node IDs)
- [ ] Direction specified (TB/LR/RL/BT for flowcharts)

## Conservative Syntax Rules

To ensure diagrams render correctly:

1. Use simple node IDs without special characters
2. Avoid complex Unicode in labels
3. Keep nesting depth ≤ 3 levels
4. Test rendering mentally before outputting

[Rest of skill content...]
```

---

## Writing Style Guide for Bulletproof Skills

### Base Writing Principles (from Skill Creator)

1. **Use imperative/infinitive form** - Verb-first instructions
   - ✅ "To create a skill, follow these steps"
   - ✅ "Validate metadata before generating code"
   - ❌ "You should create a skill by following"
   - ❌ "It would be good to validate metadata"

2. **Objective, instructional language** - Not conversational
   - ✅ "This skill provides guidance for..."
   - ✅ "The following steps are required..."
   - ❌ "I'll help you create skills..."
   - ❌ "Let's start by understanding..."

3. **Third-person descriptions** - For frontmatter and intros
   - ✅ "This skill should be used when creating..."
   - ❌ "Use this skill when you need to create..."

### Enforcement Writing Additions

#### Visual Markers

Use consistent visual markers throughout enforcement blocks:

- **⛔** - STOP/blocking condition (first-line blockers, gate blocks)
- **🚨** - Critical warning or consequence declaration
- **🔒** - Gate/checkpoint (multi-step workflows)
- **✅** - Confirmation/success message (output after completing step)
- **❌** - Violation/error (consequences, failure modes)
- **✋** - Pause point (checkpoints within gates)
- **🗺️** - Routing/branching (conditional workflows)
- **✓** - Checklist (verification lists)
- **📋** - Configuration (YAML blocks)

#### Imperative Language for Enforcement

Write enforcement instructions with strong imperative verbs:

**Strong (use these)**:
- MUST, EXECUTE, STOP, REQUIRED, MANDATORY
- DO NOT, NEVER, ALWAYS
- VERIFY, VALIDATE, CONFIRM, CHECK

**Weak (avoid these)**:
- should, could, might, consider
- it would be good to, please, perhaps
- you may want to, optionally

**Examples**:

✅ **Strong enforcement**:
```markdown
## ⛔ MANDATORY VALIDATION

**YOU MUST execute these checks before proceeding:**
1. VERIFY file exists
2. VALIDATE file format
3. CONFIRM write permissions

**DO NOT proceed without completing all checks.**
```

❌ **Weak enforcement**:
```markdown
## Validation

You should probably check that the file exists and has the right format. It would be good to verify permissions too.
```

#### Confirmation Message Format

Use consistent format for confirmation messages:

**Template**: `✅ [Component/Step name]: [Brief description of what was confirmed]`

**Examples**:
```markdown
✅ Gate 1 cleared: Metadata validated
✅ Pre-action verification complete: All prerequisites met
✅ Skills Index loaded
✅ API validation complete: No hallucinated methods detected
✅ Routing activated: File operations workflow selected
```

#### Consequence Declaration Format

Use structured format for declaring consequences:

**Template**:
```markdown
## 🚨 Enforcement & Consequences

```yaml
ENFORCEMENT_LEVEL: [CRITICAL|HIGH|MEDIUM|LOW]
VIOLATION_CONSEQUENCE: [One-sentence description]
SCOPE: [When this applies]
```

**Consequences of Violation:**

IF [condition]:
- ❌ [Consequence 1]
- ❌ [Consequence 2]
- ❌ [Consequence 3]

**[COMPLIANCE/VALIDATION/ACCURACY] IS NOT OPTIONAL**
```

**Example**:
```markdown
## 🚨 Enforcement & Consequences

```yaml
ENFORCEMENT_LEVEL: CRITICAL
VIOLATION_CONSEQUENCE: Generated code will fail compilation
SCOPE: All 1C BSL code generation
```

**Consequences of Violation:**

IF you generate code without MCP validation:
- ❌ Code is INVALID and will be rejected
- ❌ Compilation errors are likely
- ❌ Runtime failures may occur
- ❌ User will request restart with proper validation

**API VALIDATION IS NOT OPTIONAL**
```

#### Checklist Format

Use YAML format for machine-readable checklists:

**Template**:
```markdown
## [Checklist Name]

```yaml
Checklist:
  - [ ] [Item 1 with action verb]
  - [ ] [Item 2 with action verb]
  - [ ] [Item 3 with action verb]

Status: [READY / BLOCKED / IN_PROGRESS]
```

**IF any unchecked:**
- Action: [What to do]
- Reason: [Why blocked]

**IF all checked:**
- Output: "✅ [Checklist name] complete"
- Proceed with: [Next action]
```

#### Gate Format

Use consistent structure for gate systems:

**Template**:
```markdown
## 🔒 [Workflow Name] Gate System

### Gate 1: [Step Name] ✋ STOP HERE FIRST
- **Action**: [Specific action with tool/command]
- **Verify**: [What to check]
- **Confirmation**: "Gate 1 cleared: [brief description]"

### Gate 2: [Step Name] ✋ STOP HERE SECOND
- **Action**: [Specific action]
- **Verify**: [What to check]
- **Confirmation**: "Gate 2 cleared: [brief description]"

[Additional gates...]

## 🚦 Final Checkpoint

**Verify all gates cleared:**
```
✅ GATES STATUS
- Gate 1: [CLEARED / BLOCKED]
- Gate 2: [CLEARED / BLOCKED]
- Gate N: [CLEARED / BLOCKED]

Ready to proceed: [YES / NO]
```

**IF ANY GATE BLOCKED:**
- ❌ STOP immediately
- Complete: [Missing gate]
- Then: Resume from next gate
```

---

## Summary: Creating Bulletproof Skills

### Core Methodology (from Skill Creator)

1. Understand with concrete examples
2. Plan reusable contents (scripts/references/assets)
3. Initialize with proper structure
4. Edit with clear instructions
5. Package with validation
6. Iterate based on feedback

### Enforcement Enhancements (NEW)

1. **Select enforcement level** - Based on skill criticality
2. **Choose strategies** - Use Decision Matrix to select 1-6
3. **Implement enforcement blocks** - Add blockers, gates, checklists as needed
4. **Declare consequences** - Make violations explicit
5. **Test compliance** - Verify enforcement mechanisms work
6. **Iterate enforcement** - Adjust strictness based on real usage

### Key Principles

- **Progressive Disclosure** - Metadata → SKILL.md → Resources
- **Enforcement-First** - Critical skills need strong compliance guarantees
- **Machine-Readable** - Use YAML for configurations and checklists
- **Visual Clarity** - Consistent markers (⛔🚨✅❌) guide attention
- **Explicit Consequences** - Agents understand what happens on violation

### When to Use Which Strategies

| Enforcement Level | Strategies | Use Case |
|------------------|-----------|----------|
| CRITICAL | 1, 2, 3, 5, 6 | Security, data integrity, legal compliance |
| HIGH | 2, 3, 4, 6 | API integrations, complex workflows, code generation |
| MEDIUM | 3, 4 | Multi-step processes, multi-tool operations |
| LOW | 3 | Simple utilities, read-only operations |

### Final Checklist for Skill Creators

Before releasing a skill:

```yaml
Skill Quality Checklist:
  Functionality:
    - [ ] All 6 steps of creation process completed
    - [ ] Concrete examples documented
    - [ ] Reusable contents identified and created
    - [ ] Instructions are clear and actionable
  
  Enforcement (if CRITICAL or HIGH):
    - [ ] Enforcement level declared in frontmatter
    - [ ] Appropriate strategies implemented (1-6)
    - [ ] Consequences explicitly stated
    - [ ] Gates/checkpoints have confirmations
    - [ ] Visual markers used consistently
    - [ ] Tested with intentional violations
  
  Structure:
    - [ ] YAML frontmatter complete
    - [ ] Progressive disclosure respected
    - [ ] Scripts/references/assets properly organized
    - [ ] File naming conventions followed
  
  Style:
    - [ ] Imperative/infinitive form used
    - [ ] Third-person descriptions
    - [ ] Enforcement language is strong (MUST, NEVER, etc.)
    - [ ] Confirmation messages formatted consistently

Status: [READY / NEEDS_WORK]
```

---

**This skill combines the proven Skill Creator methodology with bulletproof enforcement techniques. Use it to create skills that agents reliably execute with strong compliance guarantees.**

