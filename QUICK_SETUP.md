# Quick Setup Guide

## 🚀 5-Minute Setup

### 1. Setup Anthropics Skills
```powershell
cd "D:\My Projects\FrameWork Global\LLM Skills"
git clone https://github.com/anthropics/skills.git anthropics-skills
```

### 2. Copy Global Rule
```powershell
Copy-Item "D:\My Projects\FrameWork Global\LLM Skills\SKILLS RULE.md" `
          "C:\Users\$env:USERNAME\AppData\Roaming\Cursor\User\SKILLS RULE.md"
check pls, not testing correct cursor catalog
```

### 3. Test Setup
Ask Cursor: *"Write a PowerShell script to check Docker status"*

**Expected**: Agent mentions reading Skills index.md and applying POWERSHELL_RULES.md

### 4. Verify Skills Work
- ✅ Agent reads Skills index.md
- ✅ Detects relevant keywords
- ✅ Studies skill files (including anthropics-skills)
- ✅ Applies correct syntax
- ✅ Mentions which skill was used

## 🎯 Key Files
- `Skills index.md` - Main skills registry
- `custom-skills/POWERSHELL_RULES.md` - PowerShell rules
- `custom-skills/DOCKER_SKILLS.md` - Docker operations
- `SKILLS RULE.md` - Global enforcement
- `anthropics-skills/` - Official Anthropic skills (excluded from git)

## 🔧 If Not Working
1. Check file locations
2. Verify anthropics-skills is cloned
3. Restart Cursor
4. Test with explicit keywords
5. Verify global rule is active

## 🆕 Creating New Skills
Use official Anthropic tools:
- `anthropics-skills/skill-creator/` - Generate from chat data
- `anthropics-skills/template-skill/` - Basic template

**You're awesome!** 🎉
