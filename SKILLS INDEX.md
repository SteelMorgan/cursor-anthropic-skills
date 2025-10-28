# Skills Index

## 📂 PATH CONVENTION
**All paths in this file are relative to workspace root (project root directory).**
- Workspace root is detected automatically
- Format: `folder/subfolder/file.md`
- Use forward slashes `/` even on Windows
- Paths start from workspace root, NOT from this file location

## 🚨 CRITICALLY IMPORTANT - MANDATORY READING 🚨
**AGENT MUST READ THIS FILE BEFORE ANY RESPONSE!**

### AUTOMATIC REQUEST ANALYSIS
**MANDATORY** to analyze user request using BOTH keyword detection AND semantic analysis:

#### 🔍 KEYWORD DETECTION SYSTEM
When detecting the following words/phrases in request - **MANDATORY** to study corresponding skill:

#### 🧠 SEMANTIC ANALYSIS SYSTEM
Analyze request meaning and context, not just keywords:

**Script Creation/Execution:**
- "create script", "write script", "execute command", "run script"
→ **MANDATORY** to study: `custom-skills/POWERSHELL_RULES.md`

**Docker Operations:**
- "manage containers", "docker compose", "container status", "docker health"
→ **MANDATORY** to study: `custom-skills/DOCKER_SKILLS.md`

**Web Development:**
- "build website", "create web app", "make UI", "frontend"
→ **MANDATORY** to study: `anthropics-skills/artifacts-builder/SKILL.md`

**Browser Automation:**
- "automate browser", "scrape website", "test web page"
→ **MANDATORY** to study: `anthropics-skills/webapp-testing/SKILL.md`

**Document Processing:**
- "create document", "generate report", "make presentation"
→ **MANDATORY** to study: corresponding document skills

**Testing:**
- "test application", "check functionality", "validate"
→ **MANDATORY** to study: `anthropics-skills/webapp-testing/SKILL.md`

**1C Development:**
- "generate 1C code", "create BSL procedure", "write 1C query", "validate BSL", "1C metadata"
→ **MANDATORY** to study: `custom-skills/1C_BSL_SKILL.md`

**PowerShell/Windows:**
- `powershell`, `ps1`, `windows`, `cmd`, `bat`, `gradlew`
→ **MANDATORY** to study: `custom-skills/POWERSHELL_RULES.md`

**Docker Operations:**
- `docker`, `container`, `docker-compose`, `image`, `volume`
→ **MANDATORY** to study: `custom-skills/DOCKER_SKILLS.md`

**Web Development:**
- `html`, `react`, `tailwind`, `artifact`, `webapp`, `ui`
→ **MANDATORY** to study: `anthropics-skills/artifacts-builder/SKILL.md`

**Browser Automation:**
- `playwright`, `scraping`, `automation`, `browser`, `docker`
→ **MANDATORY** to study: `anthropics-skills/webapp-testing/SKILL.md`

**Documents:**
- `docx`, `word`, `document` → `anthropics-skills/document-skills/docx/SKILL.md`
- `pdf`, `adobe` → `anthropics-skills/document-skills/pdf/SKILL.md`
- `xlsx`, `excel`, `spreadsheet` → `anthropics-skills/document-skills/xlsx/SKILL.md`
- `pptx`, `powerpoint`, `presentation` → `anthropics-skills/document-skills/pptx/SKILL.md`

**Creative:**
- `art`, `visual`, `design`, `gif`, `animation` → corresponding creative skills

**Testing:**
- `test`, `testing`, `webapp` → `anthropics-skills/webapp-testing/SKILL.md`

**1C/BSL Development:**
- `1с`, `bsl`, `1c:enterprise`, `справочник`, `документ`, `регистр`, `запрос`
→ **MANDATORY** to study: `custom-skills/1C_BSL_SKILL.md`

### ⚡ MANDATORY VERIFICATION
**BEFORE RESPONSE AGENT MUST:**
1. ✅ Read this file FIRST
2. ✅ Analyze request using BOTH keyword detection AND semantic analysis
3. ✅ Study corresponding skill file if ANY match found
4. ✅ Apply knowledge from skill in response
5. ✅ Mention which skill was used and why (keyword or semantic match)
6. ✅ Show evidence of skill application in code/commands
7. ✅ Use correct syntax from skill rules

**ANALYSIS REQUIREMENTS:**
- Check for exact keyword matches
- Analyze request meaning and intent
- Consider context and implied tasks
- Apply most relevant skill even if no exact keywords
- **MUST** reference skill file in response
- **MUST** show which rules were applied

**EXAMPLE OF CORRECT RESPONSE:**
"I read Skills index.md and detected PowerShell keywords. I studied custom-skills/POWERSHELL_RULES.md and applied the following rules: [list rules]. Here's the script using proper PowerShell syntax..."

**🚨 VIOLATION = CRITICAL ERROR - AGENT WILL BE REPRIMANDED! 🚨**

## Custom Skills (Project-Specific)
- **powershell-scripts** → `custom-skills/POWERSHELL_RULES.md`
  - PowerShell command generation in Windows
- **docker-operations** → `custom-skills/DOCKER_SKILLS.md`
  - Docker container and service management
- **1c-bsl-development** → `custom-skills/1C_BSL_SKILL.md`
  - 1C:Enterprise (BSL) code generation with anti-hallucination validation

## Skills Collection
**All paths relative to workspace root**

### Creative & Design
- **algorithmic-art** → `anthropics-skills/algorithmic-art/SKILL.md`
  - Creating algorithmic art with p5.js, interactive parameters
- **canvas-design** → `anthropics-skills/canvas-design/SKILL.md`
  - Creating visual art in .png/.pdf formats
- **slack-gif-creator** → `anthropics-skills/slack-gif-creator/SKILL.md`
  - Creating animated GIFs for Slack with size validators

### Development & Technical
- **artifacts-builder** → `anthropics-skills/artifacts-builder/SKILL.md`
  - Creating complex HTML artifacts with React, Tailwind CSS, shadcn/ui
- **mcp-builder** → `anthropics-skills/mcp-builder/SKILL.md`
  - Creating MCP servers for external API integration
- **playwright-docker-automation** → `anthropics-skills/webapp-testing/SKILL.md`
  - Browser automation using Playwright in Docker containers for web scraping and testing
- **webapp-testing** → `anthropics-skills/webapp-testing/SKILL.md`
  - Testing web applications with Playwright

### Enterprise & Communication
- **brand-guidelines** → `anthropics-skills/brand-guidelines/SKILL.md`
  - Applying Anthropic brand colors and typography
- **internal-comms** → `anthropics-skills/internal-comms/SKILL.md`
  - Writing internal communications (reports, updates, FAQ)
- **theme-factory** → `anthropics-skills/theme-factory/SKILL.md`
  - Styling artifacts with themes (10 ready-made + creating new ones)

### Meta Skills
- **skill-creator** → `anthropics-skills/skill-creator/SKILL.md`
  - Creating effective skills for extending agent capabilities
- **template-skill** → `anthropics-skills/template-skill/SKILL.md`
  - Basic template for creating new skills

### Document Skills
- **docx** → `anthropics-skills/document-skills/docx/SKILL.md`
  - Creating/editing .docx with change tracking
- **pdf** → `anthropics-skills/document-skills/pdf/SKILL.md`
  - PDF manipulations: extraction, creation, merging, forms
- **pptx** → `anthropics-skills/document-skills/pptx/SKILL.md`
  - Creating/editing presentations with templates and charts
- **xlsx** → `anthropics-skills/document-skills/xlsx/SKILL.md`
  - Working with spreadsheets: formulas, data analysis, visualization

## Usage
- **Creative**: algorithmic-art, canvas-design, slack-gif-creator
- **Development**: artifacts-builder, mcp-builder, playwright-docker-automation, webapp-testing  
- **Business**: brand-guidelines, internal-comms, theme-factory
- **Documents**: docx, pdf, pptx, xlsx
- **Meta**: skill-creator, template-skill
