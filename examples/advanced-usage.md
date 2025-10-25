# Продвинутые примеры использования

## Создание собственных навыков

### 1. Использование skill-creator

```bash
# Переход в директорию skill-creator
cd "D:\My Projects\FrameWork Global\LLM Skills\anthropics-skills\skill-creator"

# Создание нового навыка
python scripts/init_skill.py my-custom-skill --path "D:\My Projects\FrameWork Global\LLM Skills\custom-skills"
```

### 2. Структура навыка

```
my-custom-skill/
├── SKILL.md                    # Основной файл навыка
│   ├── YAML frontmatter        # Метаданные
│   └── Markdown инструкции     # Описание и правила
├── scripts/                    # Исполняемые скрипты
│   └── example.py
├── references/                 # Справочная документация
│   └── api-docs.md
└── assets/                     # Ресурсы для вывода
    └── templates/
```

### 3. Пример SKILL.md

```yaml
---
name: my-custom-skill
description: This skill should be used when users need to perform specific custom operations.
license: Complete terms in LICENSE.txt
---

# My Custom Skill

## When to use this skill
Use this skill when:
- User requests custom operations
- Specific domain knowledge is needed
- Automated workflows are required

## How to use this skill

1. **Identify the operation type** from the request
2. **Load appropriate scripts** from `scripts/` directory
3. **Reference documentation** from `references/` directory
4. **Apply domain-specific rules** and patterns

## Keywords
custom, operation, domain-specific, automation
```

## Интеграция с существующими навыками

### 1. Комбинирование навыков

**Запрос:** "Создай PowerShell скрипт для автоматизации Docker контейнеров с веб-интерфейсом"

**Применяемые навыки:**
- `POWERSHELL_RULES.md` - для синтаксиса PowerShell
- `DOCKER_SKILLS.md` - для операций с Docker
- `artifacts-builder/SKILL.md` - для веб-интерфейса

### 2. Каскадное применение

```
1. Обнаружение ключевых слов → PowerShell + Docker + Web
2. Загрузка соответствующих навыков
3. Применение правил из каждого навыка
4. Создание интегрированного решения
```

## Специализированные конфигурации

### 1. Для разработчиков

Создайте `Skills-Index-Developer.md`:

```markdown
# Developer Skills Index

## Development Skills
- **artifacts-builder** → React/Tailwind веб-приложения
- **webapp-testing** → Тестирование веб-приложений
- **mcp-builder** → Создание MCP серверов

## Automation Skills
- **playwright-docker-automation** → Автоматизация браузера
- **POWERSHELL_RULES.md** → Windows скрипты
- **DOCKER_SKILLS.md** → Контейнеризация

## Keywords for Developers
`react`, `typescript`, `testing`, `automation`, `docker`, `powershell`
```

### 2. Для аналитиков

Создайте `Skills-Index-Analyst.md`:

```markdown
# Analyst Skills Index

## Document Skills
- **docx** → Создание отчетов
- **pdf** → Анализ документов
- **xlsx** → Работа с данными
- **pptx** → Презентации

## Communication Skills
- **internal-comms** → Внутренние коммуникации
- **brand-guidelines** → Корпоративный стиль

## Keywords for Analysts
`report`, `analysis`, `document`, `presentation`, `data`
```

## Мониторинг и отладка

### 1. Проверка применения навыков

```powershell
# Проверка структуры проекта
Get-ChildItem "D:\My Projects\FrameWork Global\LLM Skills" -Recurse | 
Where-Object {$_.Name -like "*SKILL*" -or $_.Name -like "*index*"}

# Проверка антропических навыков
Test-Path "D:\My Projects\FrameWork Global\LLM Skills\anthropics-skills"
```

### 2. Логирование использования

Создайте скрипт для отслеживания применения навыков:

```powershell
# log-skill-usage.ps1
param(
    [string]$SkillName,
    [string]$Request,
    [string]$Response
)

$logEntry = @{
    Timestamp = Get-Date
    Skill = $SkillName
    Request = $Request
    ResponseLength = $Response.Length
}

$logEntry | ConvertTo-Json | Add-Content "skill-usage.log"
```

## Оптимизация производительности

### 1. Кэширование навыков

```powershell
# Создание кэша навыков
$skillsCache = @{}
$skillsPath = "D:\My Projects\FrameWork Global\LLM Skills"

Get-ChildItem "$skillsPath\custom-skills\*.md" | ForEach-Object {
    $skillName = $_.BaseName
    $skillsCache[$skillName] = Get-Content $_.FullName -Raw
}
```

### 2. Предзагрузка часто используемых навыков

```powershell
# Предзагрузка основных навыков
$prioritySkills = @("POWERSHELL_RULES", "DOCKER_SKILLS")
$prioritySkills | ForEach-Object {
    $skillPath = "D:\My Projects\FrameWork Global\LLM Skills\custom-skills\$_.md"
    if (Test-Path $skillPath) {
        Write-Host "Preloading skill: $_"
        # Логика предзагрузки
    }
}
```

## Расширенные сценарии

### 1. Автоматическое создание навыков из чата

```python
# create-skill-from-chat.py
import json
import os

def create_skill_from_chat(chat_data, skill_name):
    """Создает навык на основе данных чата"""
    
    # Анализ паттернов в чате
    patterns = analyze_chat_patterns(chat_data)
    
    # Создание структуры навыка
    skill_structure = {
        "name": skill_name,
        "description": generate_description(patterns),
        "keywords": extract_keywords(patterns),
        "rules": extract_rules(patterns)
    }
    
    # Генерация SKILL.md
    generate_skill_file(skill_structure)
```

### 2. Интеграция с внешними API

```powershell
# Интеграция с GitHub API для обновления навыков
$headers = @{
    "Authorization" = "token $env:GITHUB_TOKEN"
    "Accept" = "application/vnd.github.v3+json"
}

$response = Invoke-RestMethod -Uri "https://api.github.com/repos/anthropics/skills" -Headers $headers
Write-Host "Latest commit: $($response.updated_at)"
```

Эти примеры демонстрируют продвинутые возможности фреймворка навыков для создания специализированных решений.
