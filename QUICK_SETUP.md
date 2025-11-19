# Quick Setup Guide

## 🚀 5-Minute Setup

### 1. Setup Anthropics Skills
```powershell
cd "D:\My Projects\FrameWork Global\LLM Skills"
git clone https://github.com/anthropics/skills.git anthropics-skills
```

### 2. Setup Claude Code Skills (Optional)
```powershell
cd "D:\My Projects\FrameWork Global\LLM Skills"
git clone https://github.com/davila7/claude-code-templates.git claude-code-templates
```

### 3. Install Global Rule

**⚠️ CRITICAL**: Текст файла `SKILLS RULE.md` должен быть добавлен как **глобальное USER RULE** в Cursor.

**Как это сделать:**
1. Откройте файл `SKILLS RULE.md`
2. Скопируйте весь его содержимое
3. В Cursor перейдите в настройки → Rules → Global Rules (или Project Rules)
4. Добавьте скопированный текст как новое правило

**Почему это важно:**
- Именно на основании `SKILLS RULE.md` агент начнет использовать Skills Index
- Агент будет автоматически подгружать навыки из индекса при обнаружении соответствующих ключевых слов
- Без этого правила агент не будет использовать систему навыков

### 4. Test Setup
Ask Cursor: *"Write a PowerShell script to check Docker status"*

**Expected**: Agent mentions reading Skills index.md and applying POWERSHELL_RULES.md

### 5. Verify Skills Work
- ✅ Agent reads Skills index.md
- ✅ Detects relevant keywords
- ✅ Studies skill files (including anthropics-skills)
- ✅ Applies correct syntax
- ✅ Mentions which skill was used

## 🎯 Key Files
- `SKILLS INDEX.md` - Main skills registry (обновить пути после клонирования!)
- `SKILLS RULE.md` - Global enforcement rule (добавить в Cursor как USER RULE)
- `custom-skills/` - Project-specific custom skills
  - `POWERSHELL_RULES.md` - PowerShell rules
  - `DOCKER_SKILLS.md` - Docker operations
  - `1C_BSL_SKILL.md` - 1C/BSL development
  - `DEVELOPMENT_METHODOLOGY_RULE.md` - SDD/TDD/DDD methodology
  - `YAXUNIT_TESTING_SKILL.md` - YAxUnit testing framework
- `anthropics-skills/` - Official Anthropic skills (excluded from git)
- `claude-code-templates/` - Claude Code templates (excluded from git)

## 🔧 If Not Working
1. **Verify SKILLS RULE.md is added as USER RULE in Cursor** (most common issue!)
2. Check file locations and paths in `SKILLS INDEX.md`
3. Verify `anthropics-skills/` is cloned
4. Verify `claude-code-templates/` is cloned (if using Claude Code skills)
5. **Update absolute paths in `SKILLS INDEX.md`** to match your workspace location
6. Restart Cursor
7. Test with explicit keywords (e.g., "powershell", "docker", "1c")
8. Verify global rule is active in Cursor settings

## 📝 Important Notes

**⚠️ After cloning repository:**
- You MUST update absolute paths in `SKILLS INDEX.md` to match your workspace location
- Replace `D:\My Projects\FrameWork Global\LLM Skills\` with your actual path

**⚠️ Critical setup step:**
- `SKILLS RULE.md` MUST be added as USER RULE in Cursor (not just copied as file!)
- Without this, the skills framework will not work

## 🆕 Creating New Skills
Use official Anthropic tools:
- `anthropics-skills/skill-creator/` - Generate from chat data
- `anthropics-skills/template-skill/` - Basic template
- `custom-skills/USER_SKILL_RULE_V2.md` - Skill creation guidelines

**You're awesome!** 🎉
