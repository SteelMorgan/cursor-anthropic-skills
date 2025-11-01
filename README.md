# Cursor Skills Framework

A comprehensive framework for ensuring AI agents in Cursor always use relevant skills and knowledge bases when responding to user requests.

## 🚨 Problem Solved

By default, Cursor AI agents may not consistently apply specialized knowledge from skill files, leading to:
- Generic responses without domain-specific expertise
- Incorrect syntax or commands (e.g., bash syntax in PowerShell)
- Missing best practices and established patterns
- Inconsistent quality across different types of requests

## 🎯 Solution

This framework enforces mandatory skill usage through:
- **Automatic keyword detection** - Identifies relevant skills by keywords
- **Semantic analysis** - Understands request intent and context
- **Mandatory skill application** - Forces agents to use appropriate knowledge
- **Verification system** - Ensures skills are properly applied

## 📁 Framework Structure

```
D:\My Projects\FrameWork Global\LLM Skills\
├── Skills index.md                    # Main skills registry and rules
├── SKILLS RULE.md                   # Global enforcement rule
├── .gitignore                        # Excludes third-party skill repositories
├── custom-skills\                    # Project-specific custom skills
│   ├── POWERSHELL_RULES.md          # PowerShell-specific rules
│   └── DOCKER_SKILLS.md             # Docker operations and management
├── anthropics-skills\               # Clone of https://github.com/anthropics/skills
│   ├── artifacts-builder\           # Complex HTML artifacts with React/Tailwind
│   ├── playwright-docker-automation\ # Browser automation in Docker
│   ├── document-skills\             # Document creation (docx, pdf, xlsx, pptx)
│   ├── skill-creator\               # Guide for creating new skills
│   ├── template-skill\              # Basic skill template
│   └── ...                          # Other official Anthropic skills
└── claude-code-templates\           # Clone of https://github.com/davila7/claude-code-templates (Claude Code skills)
```

### 🔗 Anthropics Skills Repository

The `anthropics-skills/` directory should contain a clone of the official [Anthropic Skills repository](https://github.com/anthropics/skills). This repository contains production-ready skills developed by Anthropic, including:

- **Document Skills**: Advanced document creation and manipulation
- **Development Skills**: Web development, testing, automation
- **Creative Skills**: Art generation, design tools
- **Meta Skills**: Skill creation and templates

### 🔗 Claude Code Templates Repository

The `claude-code-templates/` directory hosts a clone of [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates). `Skills index.md` now lists the unique and extended Claude skills that complement the Anthropic catalog:

- **Git Commit Helper**: Generate commit messages based on `git diff`
- **Email Composer**: Draft professional email templates
- **Excel Analysis**: Provide quick pandas-based spreadsheet reviews
- **PDF Processing**: Offer lightweight recipes for extracting and merging PDFs
- **PDF Processing Pro**: Deliver an advanced pipeline with CLI scripts, OCR, and validation

Mirrored Anthropics skills (for example, `docx`, `artifacts-builder`) also live in the Claude Code repository, which is why the directory is excluded from Git via `.gitignore`.

**Setup Options:**
1. **Clone Official Repository**: `git clone https://github.com/anthropics/skills.git anthropics-skills`
2. **Download Specific Skills**: Copy only the skills you need
3. **Create Custom Skills**: Use the `skill-creator` and `template-skill` as guides

## 🛠️ Setup Instructions

### Step 1: Setup Anthropics Skills

Clone the official Anthropic skills repository:

```powershell
# Navigate to the skills directory
cd "D:\My Projects\FrameWork Global\LLM Skills"

# Clone the official repository
git clone https://github.com/anthropics/skills.git anthropics-skills

# Or download specific skills you need
# The repository contains production-ready skills from Anthropic
```

**Important**: The `anthropics-skills/` directory is excluded from version control via `.gitignore` to avoid committing third-party code.

### Step 2: Setup Claude Code Skills

Clone the Claude Code templates repository so that `Skills index.md` can reference the extended skills:

```powershell
# Navigate to the skills directory
cd "D:\My Projects\FrameWork Global\LLM Skills"

# Clone Claude Code skills collection
git clone https://github.com/davila7/claude-code-templates.git claude-code-templates
```

**Note**: The `claude-code-templates/` directory is also added to `.gitignore` to avoid committing third-party templates.

### Step 3: Install Global Rule

Copy the critical skills rule to Cursor's global configuration / project configuration / role-custom-agent instructions

### Step 4: Verify and Update Skills Index

⚠️ **CRITICAL STEP**: Update absolute paths in `Skills index.md`

After cloning/moving this repository to your location, you MUST update all absolute paths in `Skills index.md` to match your workspace location.

**Option 1: Use automated script (Recommended)**

Run the provided PowerShell script to automatically update all paths:

```powershell
# Navigate to the skills directory
cd "YOUR_ACTUAL_PATH"

# Run the update script (it will auto-detect your current path)
.\update-paths.ps1

# Or specify custom path explicitly
.\update-paths.ps1 -NewPath "C:\Your\Custom\Path\"
```

**Option 2: Manual update**

1. Open `Skills index.md`
2. Find and replace all occurrences of the base path:
   - Old path: `D:\My Projects\FrameWork Global\LLM Skills\`
   - New path: `YOUR_ACTUAL_PATH\` (e.g., `C:\Projects\LLM Skills\`)

3. Example PowerShell command for manual update:
```powershell
# Navigate to the skills directory
cd "YOUR_ACTUAL_PATH"

# Replace old path with your new path (PowerShell)
$oldPath = "D:\\My Projects\\FrameWork Global\\LLM Skills\\"
$newPath = "YOUR_ACTUAL_PATH\\"
(Get-Content "Skills index.md") -replace [regex]::Escape($oldPath), $newPath | Set-Content "Skills index.md"
```

**Verify Skills Index contains:**
- 🚨 Critical importance warnings
- 🔍 Keyword detection system
- 🧠 Semantic analysis rules
- ⚡ Mandatory verification steps
- 📚 References to anthropics-skills (with UPDATED absolute paths)

### Step 5: Test the Setup

⚠️ **IMPORTANT**: Use a complex test request, NOT a simple one. Simple requests may cause the agent to skip skill usage.

Use this test request to verify the framework works:

```
Write a PowerShell script that checks Docker container status, waits 5 seconds, then makes an HTTP request to localhost:8080/health. If the service doesn't respond, the script should output an error.
```

**Expected behavior:**
- Agent reads Skills index.md
- Detects PowerShell keywords
- Studies POWERSHELL_RULES.md
- Applies PowerShell-specific syntax
- Mentions which skill was used

**Why this test works:**
- ✅ Complex multi-step task
- ✅ Combines Docker + PowerShell + HTTP request
- ✅ Requires domain-specific knowledge
- ✅ Forces agent to consult skill files

## 🔍 How It Works

### 1. Keyword Detection
The system automatically detects relevant skills based on keywords:

| Keywords | Skill Applied |
|----------|---------------|
| `powershell`, `ps1`, `script`, `windows` | POWERSHELL_RULES.md |
| `html`, `react`, `webapp`, `ui` | artifacts-builder/SKILL.md |
| `playwright`, `automation`, `browser` | playwright-docker-automation/SKILL.md |
| `document`, `docx`, `pdf`, `xlsx` | document-skills/ |
| `test`, `testing` | webapp-testing/SKILL.md |

### 2. Semantic Analysis
Beyond keywords, the system understands intent:

| Request Intent | Skill Applied |
|----------------|---------------|
| "Create a script" | PowerShell skills |
| "Build a website" | Web development skills |
| "Test my app" | Testing skills |
| "Generate a document" | Document skills |
| "Automate browser" | Playwright skills |

### 3. Mandatory Application
When a relevant skill is detected, the agent MUST:
- ✅ Read the corresponding skill file
- ✅ Apply knowledge from the skill
- ✅ Use correct syntax/commands
- ✅ Mention which skill was used
- ✅ Show evidence of skill application

## 📋 Available Skills

### Custom Skills (Project-Specific)
- **PowerShell & Windows**: `custom-skills/POWERSHELL_RULES.md`
  - **Keywords**: `powershell`, `ps1`, `windows`, `cmd`, `bat`, `gradlew`
  - **Rules**: Command separation, path quoting, HTTP requests, error handling

- **Docker Operations**: `custom-skills/DOCKER_SKILLS.md`
  - **Keywords**: `docker`, `container`, `docker-compose`, `image`, `volume`
  - **Rules**: Container management, compose operations, health checks, PowerShell integration

Check and actualize PS & Docker skills for yourself (this is only my example)

### Official Anthropic Skills (Production-Ready)


## 🧪 Testing the Framework

⚠️ **IMPORTANT: Use Complex Test Cases**

When testing the skills framework, **DO NOT use overly simple requests**. Simple tasks may cause the agent to skip skill usage because:
- The agent considers simple tasks trivial and not requiring specialized knowledge
- Skills and project rules may be ignored for straightforward requests
- The framework is designed for complex, multi-step tasks requiring domain expertise

**❌ Bad test examples (too simple):**
- "Write hello world in PowerShell"
- "Create a simple HTML page"
- "Show me a Docker command"

**✅ Good test examples (sufficiently complex):**
- "Write a PowerShell script that checks Docker container status, waits 5 seconds, then makes an HTTP request to localhost:8080/health"
- "Create a React component with state management and API integration"
- "Build a Docker compose setup with health checks and volume management"

---

### Test Case 1: PowerShell Script
**Request**: "Write a PowerShell script to check system status"

**Expected Response**:
```
I read Skills index.md and detected PowerShell keywords. I studied POWERSHELL_RULES.md and applied the following rules:
- Command separation using semicolons
- Proper path quoting with double quotes
- Using Invoke-WebRequest instead of curl
- Using Start-Sleep instead of timeout

Here's the script using proper PowerShell syntax:
[script with correct PowerShell commands]
```

### Test Case 2: Web Development
**Request**: "Create a React component for user dashboard"

**Expected Response**:
```
I read Skills index.md and detected web development keywords. I studied artifacts-builder/SKILL.md and applied React and Tailwind CSS patterns.

Here's the component using proper React and Tailwind syntax:
[component with correct React/Tailwind code]
```

## 📈 Benefits

### Using Official Anthropic Skills
- **Production-Ready**: Skills used in actual Claude applications
- **Battle-Tested**: Proven in real-world scenarios
- **Standardized Format**: Follows official skill creation guidelines
- **Comprehensive Coverage**: Wide range of domains and use cases
- **Regular Updates**: Maintained by Anthropic team

### Framework Benefits
- **Consistent Quality**: All responses use appropriate domain expertise
- **Correct Syntax**: Proper commands and syntax for each technology
- **Best Practices**: Established patterns and methodologies applied
- **Verification**: Clear evidence of skill application
- **Scalability**: Easy to add new skills and domains
- **Skill Creation**: Use `skill-creator` to generate new skills from chat data

## 🔄 Maintenance

### Creating New Skills
Use the official Anthropic skill creation tools:

1. **Use skill-creator**: `anthropics-skills/skill-creator/SKILL.md`
   - Generate skills from chat data
   - Follow official skill creation guidelines
   - Ensure proper YAML frontmatter format

2. **Use template-skill**: `anthropics-skills/template-skill/SKILL.md`
   - Basic template for new skills
   - Proper structure and metadata
   - Example patterns and guidelines

3. **Add to Skills index.md**:
   - Add keywords for detection
   - Include semantic analysis rules
   - Update verification requirements

### Adding New Skills
1. Create skill file in `custom-skills/` directory using official templates
2. Add entry to Skills index.md with keywords
3. Update keyword detection system
4. Test with sample requests

### Custom Skills Structure
```
custom-skills/
├── POWERSHELL_RULES.md    # PowerShell-specific rules
├── DOCKER_SKILLS.md       # Docker operations
└── [your-custom-skill].md # Additional custom skills
```

### Updating Existing Skills
1. Modify skill file with new rules/examples
2. Update Skills index.md if keywords change
3. Test with existing use cases
4. Verify backward compatibility

### Syncing with Official Repository
```powershell
# Update anthropics-skills from official repository
cd "D:\My Projects\FrameWork Global\LLM Skills\anthropics-skills"
git pull origin main

# Or re-clone for fresh copy
cd "D:\My Projects\FrameWork Global\LLM Skills"
Remove-Item -Recurse -Force anthropics-skills
git clone https://github.com/anthropics/skills.git anthropics-skills
```

## 🎯 Specialized Skills Index for Different Roles

The Skills Index can be customized for different agent roles and project types. Instead of using a single universal Skills Index, you can create specialized versions tailored to specific use cases:


### Implementation Strategy

Combine the custom agent (role-playing skills) and developer pipeline for better results.

### Benefits of Specialized Skills Index

- **🎯 Focused Expertise**: Agents become specialists in their domain
- **⚡ Faster Responses**: Reduced cognitive load with relevant skills only
- **🔧 Better Accuracy**: Domain-specific rules and patterns
- **📈 Improved Quality**: Tailored best practices for each role
- **🚀 Scalability**: Easy to add new roles and specializations

### Example Usage

```powershell
# For Developer Agent
Copy-Item "Skills-Index-Developer.md" "Skills index.md"
Copy-Item "SKILLS RULE.md" "C:\Users\$env:USERNAME\AppData\Roaming\Cursor\User\"

# For Analyst Agent  
Copy-Item "Skills-Index-Analyst.md" "Skills index.md"
Copy-Item "SKILLS RULE.md" "C:\Users\$env:USERNAME\AppData\Roaming\Cursor\User\"
```