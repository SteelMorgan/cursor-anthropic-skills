# CRITICAL SKILLS RULE

**ABSOLUTELY MANDATORY BEFORE ANY RESPONSE**

---

## 🎯 EXECUTION FLOW (STRICTLY SEQUENTIAL)

### STEP 1: ANALYZE REQUEST
**IMMEDIATE ACTION REQUIRED:**
- 🔍 Scan user request for keywords
- 🧠 Analyze semantic meaning and intent
- 📝 Identify potential skill categories

---

### STEP 2: CONSULT SKILLS INDEX
**MANDATORY ACTIONS:**
1. ✅ Read `SKILLS INDEX.md` file
2. ✅ Match your analysis from Step 1 with skill categories in index
3. ✅ Extract **EXACT FILE PATH(S)** of matching skill(s)
4. ✅ Prepare list of skill files to read

**CRITICAL**: This step only identifies WHICH skills to use, not HOW to use them!

---

### STEP 3: READ SKILL FILES
**MANDATORY ACTIONS:**
1. ✅ **IMMEDIATELY** read ALL skill files identified in Step 2
2. ✅ Study syntax rules, commands, examples from each skill file
3. ✅ Add skill file contents to your working context
4. ✅ Prepare to apply knowledge from these files

**🚨 CRITICAL RULE**: 
- Do NOT skip this step!
- Do NOT rely only on INDEX - it's a directory, not a manual
- You MUST read the actual SKILL files (e.g., `POWERSHELL_RULES.md`, `DOCKER_SKILLS.md`, `1C_BSL_SKILL.md`, etc.)

---

### STEP 4: APPLY SKILL KNOWLEDGE
**MANDATORY ACTIONS:**
1. ✅ Use syntax/commands/patterns from skill files (not from index!)
2. ✅ Follow all rules specified in skill files
3. ✅ Generate code/commands according to skill specifications

---

### STEP 5: VERIFICATION & RESPONSE
**MANDATORY ACTIONS:**
1. ✅ Mention which skill files were used (by filename)
2. ✅ Reference specific rules from skill files that were applied
3. ✅ Show evidence of skill application in your code/commands
4. ✅ Confirm you read SKILL FILES (not just index)

**EXAMPLE OF CORRECT RESPONSE:**
```
Я прочитал SKILLS INDEX.md и обнаружил ключевые слова PowerShell в запросе.
Затем я прочитал файл custom-skills/POWERSHELL_RULES.md и применил следующие правила:
- Правило #1: Использование ; вместо && для разделения команд
- Правило #3: Использование Invoke-WebRequest вместо curl
Вот скрипт с правильным синтаксисом PowerShell...
```

---

## 🔍 KEYWORD & SEMANTIC DETECTION RULES

### PowerShell/Windows Scripts:
**Keywords**: `powershell`, `ps1`, `script`, `windows`, `cmd`, `bat`, `gradlew`
**Semantic**: "create script", "run command", "execute in Windows"
→ **ACTION**: Read `custom-skills/POWERSHELL_RULES.md`

### Docker Operations:
**Keywords**: `docker`, `container`, `docker-compose`, `image`, `volume`
**Semantic**: "manage containers", "container status", "docker health"
→ **ACTION**: Read `custom-skills/DOCKER_SKILLS.md`

### Web Development:
**Keywords**: `html`, `react`, `tailwind`, `artifact`, `webapp`, `ui`
**Semantic**: "build website", "create web app", "make UI", "frontend"
→ **ACTION**: Read `anthropics-skills/artifacts-builder/SKILL.md`

### Browser Automation:
**Keywords**: `playwright`, `automation`, `browser`, `scraping`
**Semantic**: "automate browser", "scrape website", "test web page"
→ **ACTION**: Read `anthropics-skills/webapp-testing/SKILL.md`

### Document Processing:
**Keywords**: `docx`, `pdf`, `xlsx`, `pptx`, `word`, `excel`, `powerpoint`
**Semantic**: "create document", "generate report", "make presentation"
→ **ACTION**: Read corresponding document skill file from `anthropics-skills/document-skills/`

### 1C/BSL Development:
**Keywords**: `1с`, `bsl`, `1c:enterprise`, `справочник`, `документ`, `регистр`, `запрос`
**Semantic**: "generate 1C code", "create BSL procedure", "1C metadata"
→ **ACTION**: Read `custom-skills/1C_BSL_SKILL.md`

---

## ⚠️ CRITICAL ERRORS TO AVOID

❌ **WRONG**: Reading only SKILLS INDEX.md and using it as knowledge source
✅ **CORRECT**: Reading SKILLS INDEX.md to find paths, then reading actual SKILL files

❌ **WRONG**: "I consulted the skills index"
✅ **CORRECT**: "I read SKILLS INDEX.md, identified PowerShell skill, then read custom-skills/POWERSHELL_RULES.md"

❌ **WRONG**: Applying generic knowledge about PowerShell
✅ **CORRECT**: Applying specific rules from POWERSHELL_RULES.md file

---

## 🚨 ENFORCEMENT

**VIOLATION OF THIS RULE = CRITICAL ERROR**

If you respond without:
1. Reading SKILLS INDEX.md
2. Reading identified SKILL file(s)
3. Applying knowledge from SKILL files
4. Mentioning which SKILL files were used

→ **YOUR RESPONSE IS INVALID AND WILL BE REJECTED**

---

## 📚 FILE STRUCTURE REFERENCE

```
SKILLS RULE.md (this file)
    ↓
SKILLS INDEX.md (directory/map)
    ↓
Specific SKILL files (actual knowledge):
    - custom-skills/POWERSHELL_RULES.md
    - custom-skills/DOCKER_SKILLS.md
    - custom-skills/1C_BSL_SKILL.md
    - anthropics-skills/artifacts-builder/SKILL.md
    - anthropics-skills/webapp-testing/SKILL.md
    - anthropics-skills/document-skills/*/SKILL.md
    - etc.
```

**Remember**: INDEX = directory, SKILL files = knowledge
