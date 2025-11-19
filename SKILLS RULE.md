# ⛔ EXECUTION GATE: Skills Loading Rules ⛔

## 🚨 CRITICAL BLOCKER - READ THIS FIRST

**YOU MUST EXECUTE BEFORE PROCEEDING:**

```yaml
ENFORCEMENT_LEVEL: MANDATORY
VIOLATION_CONSEQUENCE: CRITICAL_FAILURE
MODE_GUARD: Always
SCOPE: EVERY request and response
```

**COMPLIANCE CHECK:**
- [ ] I have read this entire document
- [ ] I will read Skills Index BEFORE any response
- [ ] I will identify relevant skill from user query
- [ ] I will load and apply relevant skill rules
- [ ] I will MENTION which skill was used
- [ ] I acknowledge violation = critical failure

**CONFIRMATION (output after reading):**
```
✅ Skills Loading Rules loaded
- Enforcement: MANDATORY before ANY response
- Skills Index: MUST be read first
- Skill identification: keyword + semantic analysis
- Skill application: MUST show evidence
- Mention requirement: MUST state which skill used
- Status: READY TO LOAD AND APPLY SKILLS
```

**STOP CONDITIONS:**
- IF no Skills Index loaded → STOP, read index first
- IF no relevant skill identified → STOP, ask user for clarification
- IF no skill loaded for matching keywords → STOP, load skill first
- IF response without mentioning skill → STOP, state which skill used

---

# CRITICAL SKILLS RULE

## ⛔ MANDATORY SKILLS LOADING GATE ⛔

**ABSOLUTELY MANDATORY BEFORE ANY RESPONSE:**

```python
# Step 1: Load Skills Index (MANDATORY FIRST STEP)
1. read_file("D:\\My Projects\\FrameWork Global\\LLM Skills\\Skills index.md")
2. Confirm: "✅ Skills Index loaded"

# Step 2: Analyze User Query (MANDATORY)
3. Extract KEYWORDS from user query:
   - Technical terms (powershell, BSL, react, etc.)
   - Action verbs (create, test, build, automate, etc.)
   - Domain indicators (1C, web, document, browser, etc.)
4. Analyze SEMANTIC MEANING:
   - What is user trying to accomplish?
   - What technology/platform is involved?
   - What type of work (coding, testing, documentation)?

# Step 3: Match to Skills (MANDATORY)
5. Check keywords against Skills Index
6. Identify ALL matching skills
7. Prioritize most relevant skill

# Step 4: Load Relevant Skill (MANDATORY)
8. read_file("[Path to identified skill from index]")
9. Study ALL rules from skill file
10. Confirm: "✅ Skill [name] loaded"

# Step 5: Apply Skill Rules (MANDATORY)
11. Anti-hallucination rules
12. Validation requirements
13. Tool usage protocols
14. Coding standards
15. Testing requirements

# Step 6: Evidence in Response (MANDATORY)
16. Mention skill name in response
17. Show evidence of skill application:
    - Using correct API/syntax from skill
    - Following validation workflow from skill
    - Applying standards from skill
```

**KEYWORD DETECTION (critical examples):**

| Keywords | Skill File |
|----------|------------|
| `powershell`, `ps1`, `script`, `windows`, `cmd`, `bat` | `POWERSHELL_RULES.md` |
| `1C`, `BSL`, `bsl`, `справочник`, `документ`, `регистр` | `1C_BSL_SKILL.md` |
| `html`, `react`, `webapp`, `ui`, `css`, `javascript` | `artifacts-builder/SKILL.md` |
| `playwright`, `automation`, `browser`, `e2e` | `playwright-docker-automation/SKILL.md` |
| `test`, `testing`, `тест`, `тестирование` | `webapp-testing/SKILL.md` |
| `document`, `docx`, `pdf`, `xlsx`, `word`, `excel` | Document skills |

**SEMANTIC ANALYSIS EXAMPLES:**

| User Query | Semantic Meaning | Required Skill |
|------------|------------------|----------------|
| "Create a script" | Need to write executable code | PowerShell skills |
| "Build a website" | Web development task | Web development skills |
| "Test my app" | Quality assurance task | Testing skills |
| "Generate a document" | Document creation task | Document skills |
| "Automate browser" | Browser automation task | Playwright skills |
| "Add справочник" | 1C metadata task | 1C BSL skills |
| "Разработать документ" | 1C document development | 1C BSL skills |

**BLOCKING CONDITIONS (CRITICAL - WILL STOP RESPONSE):**
- ❌ Response without reading Skills Index → STOP, read index first
- ❌ Response without loading relevant skill → STOP, load skill first
- ❌ Response without mentioning which skill was used → STOP, state skill
- ❌ Response without evidence of skill application → STOP, apply skill rules
- ❌ Response violating skill rules (e.g., hallucinating 1C API) → STOP, follow skill

**VIOLATION = CRITICAL ERROR:** Any response without this complete protocol

---

## ✅ COMPLIANCE CONFIRMATION PROTOCOL

**After reading this file completely, you MUST output:**

```
✅ skills rule enforcement complete
- Skills loading protocol: understood (6-step sequence)
- Skills Index location: D:\My Projects\FrameWork Global\LLM Skills\Skills index.md
- Keyword detection: understood (will extract and match)
- Semantic analysis: understood (will analyze intent)
- Evidence requirement: understood (will mention skill + show application)
- Blocking conditions: acknowledged
- Status: READY TO LOAD AND APPLY SKILLS FOR EVERY REQUEST
```

**IF YOU DO NOT OUTPUT THIS CONFIRMATION:**
- Your responses are considered NON-COMPLIANT
- User will reject your work
- You MUST restart and read skills rule properly

---

## EXAMPLE OF CORRECT SKILL APPLICATION

**User:** "нужно разработать новый справочник Контрагенты"

**Agent response (CORRECT):**

```
✅ Skills Index loaded
✅ Skill loaded: 1C_BSL_SKILL.md (detected keywords: "справочник", semantic: 1C metadata development)

Applying 1C BSL Skill rules:
1. Anti-hallucination: will validate ALL metadata via MCP before proposing
2. No assumptions: will use mcp_1c-metacode_search_metadata to check existing structure
3. Validation required: will use mcp_bsl-platform-context to verify API

[continues with actual work following skill rules...]
```

**This demonstrates:**
✅ Skills Index was read
✅ Relevant skill was identified (1C_BSL_SKILL.md)
✅ Keywords were detected ("справочник")
✅ Semantic meaning was analyzed (1C metadata development)
✅ Skill was explicitly mentioned
✅ Evidence of application (listing specific rules being followed)
