# Skills Index

**THIS IS A DIRECTORY/MAP FILE**
- This file contains ONLY paths to skill files
- This file is NOT a source of knowledge itself
- After consulting this file, you MUST read the actual SKILL files listed here

---

## 📂 PATH CONVENTION
**All paths in this file are relative to workspace root (project root directory).**
- Workspace root is detected automatically
- Format: `folder/subfolder/file.md`
- Use forward slashes `/` even on Windows
- Paths start from workspace root, NOT from this file location

---

## 🗺️ HOW TO USE THIS INDEX

### THIS FILE IS A MAP, NOT A MANUAL

1. **Analyze your request** - identify keywords and semantic meaning
2. **Find matching category** in sections below
3. **Extract file path(s)** of relevant skill(s)
4. **Read those skill files** - this is where actual knowledge is!

**Example Flow:**
```
Request: "Create a PowerShell script"
↓
Index lookup: PowerShell → custom-skills/POWERSHELL_RULES.md
↓
ACTION: Read custom-skills/POWERSHELL_RULES.md (the actual skill file!)
↓
Apply rules from that file
```

---

## 🔍 KEYWORD & SEMANTIC MAPPING

### PowerShell/Windows Scripts
**When you detect:**
- Keywords: `powershell`, `ps1`, `windows`, `cmd`, `bat`, `gradlew`, `script`
- Semantic: "create script", "run command", "execute in Windows", "batch file"

**Then read this file:**
→ `custom-skills/POWERSHELL_RULES.md`

---

### Docker Operations
**When you detect:**
- Keywords: `docker`, `container`, `docker-compose`, `image`, `volume`, `dockerfile`
- Semantic: "manage containers", "container status", "docker health", "compose up"

**Then read this file:**
→ `custom-skills/DOCKER_SKILLS.md`

---

### Web Development
**When you detect:**
- Keywords: `html`, `react`, `tailwind`, `artifact`, `webapp`, `ui`, `frontend`, `shadcn`
- Semantic: "build website", "create web app", "make UI", "design page", "interactive"

**Then read this file:**
→ `anthropics-skills/artifacts-builder/SKILL.md`

---

### Browser Automation & Testing
**When you detect:**
- Keywords: `playwright`, `automation`, `browser`, `scraping`, `testing`, `selenium`
- Semantic: "automate browser", "scrape website", "test web page", "click button", "fill form"

**Then read this file:**
→ `anthropics-skills/webapp-testing/SKILL.md`

---

### 1C/BSL Development
**When you detect:**
- Keywords: `1с`, `bsl`, `1c:enterprise`, `справочник`, `документ`, `регистр`, `запрос`, `процедура`, `функция`
- Semantic: "generate 1C code", "create BSL procedure", "1C metadata", "write query", "validate BSL"

**Then read this file:**
→ `custom-skills/1C_BSL_SKILL.md`

---

### Document Processing

#### Word Documents (DOCX)
**When you detect:**
- Keywords: `docx`, `word`, `document`, `.docx`
- Semantic: "create document", "write report", "make .docx"

**Then read this file:**
→ `anthropics-skills/document-skills/docx/SKILL.md`

#### PDF Documents
**When you detect:**
- Keywords: `pdf`, `adobe`, `.pdf`
- Semantic: "create PDF", "merge PDFs", "extract from PDF", "fillable forms"

**Then read this file:**
→ `anthropics-skills/document-skills/pdf/SKILL.md`

#### Excel Spreadsheets (XLSX)
**When you detect:**
- Keywords: `xlsx`, `excel`, `spreadsheet`, `.xlsx`, `csv`
- Semantic: "create spreadsheet", "analyze data", "make charts", "formulas"

**Then read this file:**
→ `anthropics-skills/document-skills/xlsx/SKILL.md`

#### PowerPoint Presentations (PPTX)
**When you detect:**
- Keywords: `pptx`, `powerpoint`, `presentation`, `.pptx`, `slides`
- Semantic: "create presentation", "make slides", "slide deck"

**Then read this file:**
→ `anthropics-skills/document-skills/pptx/SKILL.md`

---

## 📚 COMPLETE SKILLS CATALOG

### Custom Skills (Project-Specific)

| Skill | File Path | Description |
|-------|-----------|-------------|
| PowerShell Scripts | `custom-skills/POWERSHELL_RULES.md` | PowerShell command generation in Windows |
| Docker Operations | `custom-skills/DOCKER_SKILLS.md` | Docker container and service management |
| 1C/BSL Development | `custom-skills/1C_BSL_SKILL.md` | 1C:Enterprise (BSL) code generation with validation |

---

### Creative & Design Skills

| Skill | File Path | Description |
|-------|-----------|-------------|
| Algorithmic Art | `anthropics-skills/algorithmic-art/SKILL.md` | Creating algorithmic art with p5.js |
| Canvas Design | `anthropics-skills/canvas-design/SKILL.md` | Creating visual art in .png/.pdf formats |
| Slack GIF Creator | `anthropics-skills/slack-gif-creator/SKILL.md` | Creating animated GIFs for Slack |

---

### Development & Technical Skills

| Skill | File Path | Description |
|-------|-----------|-------------|
| Artifacts Builder | `anthropics-skills/artifacts-builder/SKILL.md` | Complex HTML artifacts with React, Tailwind, shadcn/ui |
| MCP Builder | `anthropics-skills/mcp-builder/SKILL.md` | Creating MCP servers for external API integration |
| Web App Testing | `anthropics-skills/webapp-testing/SKILL.md` | Browser automation using Playwright for testing/scraping |

---

### Document Skills

| Skill | File Path | Description |
|-------|-----------|-------------|
| DOCX | `anthropics-skills/document-skills/docx/SKILL.md` | Creating/editing .docx with change tracking |
| PDF | `anthropics-skills/document-skills/pdf/SKILL.md` | PDF manipulations: extraction, creation, merging, forms |
| PPTX | `anthropics-skills/document-skills/pptx/SKILL.md` | Creating/editing presentations with templates and charts |
| XLSX | `anthropics-skills/document-skills/xlsx/SKILL.md` | Working with spreadsheets: formulas, data analysis |

---

### Enterprise & Communication Skills

| Skill | File Path | Description |
|-------|-----------|-------------|
| Brand Guidelines | `anthropics-skills/brand-guidelines/SKILL.md` | Applying Anthropic brand colors and typography |
| Internal Communications | `anthropics-skills/internal-comms/SKILL.md` | Writing internal communications (reports, updates, FAQ) |
| Theme Factory | `anthropics-skills/theme-factory/SKILL.md` | Styling artifacts with ready-made and custom themes |

---

### Meta Skills

| Skill | File Path | Description |
|-------|-----------|-------------|
| Skill Creator | `anthropics-skills/skill-creator/SKILL.md` | Creating effective skills for extending agent capabilities |
| Template Skill | `anthropics-skills/template-skill/SKILL.md` | Basic template for creating new skills |

---

## 🎯 QUICK LOOKUP BY USE CASE

### "I need to create..."
- **Script/automation** → `custom-skills/POWERSHELL_RULES.md`
- **Website/web app** → `anthropics-skills/artifacts-builder/SKILL.md`
- **Document (.docx)** → `anthropics-skills/document-skills/docx/SKILL.md`
- **Presentation (.pptx)** → `anthropics-skills/document-skills/pptx/SKILL.md`
- **Spreadsheet (.xlsx)** → `anthropics-skills/document-skills/xlsx/SKILL.md`
- **PDF** → `anthropics-skills/document-skills/pdf/SKILL.md`
- **GIF animation** → `anthropics-skills/slack-gif-creator/SKILL.md`
- **1C code** → `custom-skills/1C_BSL_SKILL.md`

### "I need to manage..."
- **Docker containers** → `custom-skills/DOCKER_SKILLS.md`
- **MCP servers** → `anthropics-skills/mcp-builder/SKILL.md`

### "I need to test..."
- **Web application** → `anthropics-skills/webapp-testing/SKILL.md`
- **Browser automation** → `anthropics-skills/webapp-testing/SKILL.md`

---

## ⚠️ IMPORTANT REMINDER

**This index is a MAP, not the KNOWLEDGE itself!**

After finding paths here:
1. ✅ Extract file path(s)
2. ✅ Read those actual SKILL files
3. ✅ Apply knowledge from SKILL files (not from this index)
4. ✅ Mention which SKILL files you read in your response

**Wrong approach**: "I consulted the skills index about PowerShell"
**Correct approach**: "I found PowerShell skill in index, then read custom-skills/POWERSHELL_RULES.md"
