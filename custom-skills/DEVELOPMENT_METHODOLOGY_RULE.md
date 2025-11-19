---
name: development-methodology
description: Mandatory rule for AI agent behavior during code development, enforcing SDD (Spec Driven Development), TDD (Test Driven Development), and DDD (Domain Driven Development) principles. This rule applies to all code development tasks, requiring specification creation/update before implementation, mandatory test coverage, and strict adherence to kiro-prompts instructions for SDD. Use when developing new features, modifying existing code, or working on any software development task.
enforcement_level: CRITICAL
violation_consequence: Code changes without proper specification updates, missing test coverage, or violations of SDD/TDD/DDD principles will result in incorrect implementations, technical debt, and potential system failures. Violations must be corrected immediately before proceeding.
---

# Development Methodology Rule: SDD, TDD, DDD

## Introduction & When to Use

This rule defines mandatory behavior for AI agents during code development, enforcing strict adherence to Spec Driven Development (SDD), Test Driven Development (TDD), and Domain Driven Development (DDD) principles.

**This rule applies when:**
- Developing new features or functionality
- Modifying existing code
- Working on any software development task
- Creating or updating specifications
- Writing or updating tests
- Implementing business logic

**Keywords for detection:**
- `development`, `code`, `implement`, `feature`, `function`, `module`, `refactor`
- `specification`, `spec`, `requirement`, `design`
- `test`, `testing`, `unit test`, `tdd`
- `sdd`, `tdd`, `ddd`, `spec driven`, `test driven`, `domain driven`

**Semantic triggers:**
- Creating/editing code
- Implementing features
- Writing tests
- Updating specifications
- Refactoring code

---

## ⛔ Execution Gate (Strategy 1: First-Line Blocker)

**DO NOT PROCEED WITH ANY DEVELOPMENT TASK UNTIL YOU COMPLETE THIS:**

### Mandatory Pre-Development Checks

**1. Determine Project Type:**

```python
# MANDATORY - Execute immediately:
# Search for *.bsl files to determine if this is a 1C/BSL project
glob_file_search(glob_pattern="*.bsl")
```

**IF *.bsl files found → This is a 1C/BSL project:**
- **MANDATORY**: Read ALL three skills BEFORE starting work:
  - `custom-skills/1C_BSL_SKILL.md` - MANDATORY before generating ANY BSL code
  - `custom-skills/1c_techlog.md` - MANDATORY when working with technical logs and debugging
  - `custom-skills/YAXUNIT_TESTING_SKILL.md` - MANDATORY when writing tests for 1C
- **ACTION**: Read these files immediately
- **CONFIRMATION**: Output "✅ 1C/BSL project detected. All mandatory skills loaded: 1C_BSL_SKILL.md, 1c_techlog.md, YAXUNIT_TESTING_SKILL.md"

**IF *.bsl files NOT found → Regular project:**
- **ACTION**: Proceed with standard workflow
- **CONFIRMATION**: Output "✅ Non-1C project detected. Proceeding with standard workflow"

**2. Check for Existing Specification:**

```python
# MANDATORY - Check if specification exists
# Search for specification files (spec.md, SPEC.md, specification.md, requirements.md, etc.)
codebase_search(query="Where is the project specification or requirements document located?")
```

**IF specification exists:**
- **ACTION**: Read and analyze the specification
- **CONFIRMATION**: Output "✅ Specification found and analyzed"

**IF specification does NOT exist:**
- **ACTION**: Ask user: "No specification found. Should I create a specification following SDD principles, or proceed without one?"
- **WAIT**: For user response before proceeding
- **CRITICAL**: Agent MUST NOT make this decision independently

**DID YOU COMPLETE BOTH CHECKS? Yes / No**

**IF NO → STOP READING, EXECUTE NOW**
**IF YES → Output confirmation and continue**

---

## 🔒 Workflow Gates (Strategy 2: Checkpoint-Based Gates)

### For New Development

#### Gate 1: Specification Creation (SDD) ✋ STOP HERE FIRST

**MANDATORY ACTIONS:**
1. **Obtain kiro-prompts instructions:**
   - Check cache for kiro-prompts instructions in current session
   - If cache empty or context changed:
     - Call `mcp_kiro-prompts_list_instructions` to get available instructions list
     - Call `mcp_kiro-prompts_get_system_instruction` for ALL instruction types:
       - `complete-instructions`
       - `capabilities`
       - `guidelines`
       - `quality-standards`
       - `response-style`
       - `workflow-patterns`
     - Save to session cache
   - If MCP kiro-prompts unavailable or returns error:
     - **WARN user**: "MCP kiro-prompts unavailable. Proceeding with SDD as agent deems appropriate."
     - Continue with SDD stage without kiro-prompts instructions

2. **Create specification following kiro-prompts guidelines:**
   - Structure specification according to kiro-prompts recommendations
   - Include acceptance criteria based on quality-standards from kiro-prompts
   - Validate specification against workflow-patterns from kiro-prompts

3. **Validate specification:**
   - Check if kiro-prompts has built-in validation function
   - If yes → use it
   - If no → create checklist based on kiro-prompts instructions
   - Verify compliance with quality-standards and workflow-patterns

**CONFIRMATION**: Output "Gate 1 cleared: Specification created/updated with kiro-prompts compliance verified"

#### Gate 2: Test Creation (TDD) ✋ STOP HERE SECOND

**MANDATORY ACTIONS:**
1. **For 1C/BSL projects:**
   - **MANDATORY**: Read `custom-skills/YAXUNIT_TESTING_SKILL.md` if not already read
   - Use YAxUnit framework for unit testing
   - Follow all mandatory procedures from YAXUNIT_TESTING_SKILL.md

2. **For other languages:**
   - Search for appropriate testing framework via MCP Context7
   - Use framework appropriate for the language/technology

3. **Create tests based on specification:**
   - Write tests that verify specification requirements
   - Cover all key mechanisms
   - Follow TDD order: specification → tests → implementation

4. **Handle situations where tests cannot be written before implementation:**
   - If tests require implementation (e.g., integration tests):
     - **ASK user**: "Tests require implementation. Should I allow partial implementation for tests, or always follow strict TDD?"
   - Wait for user response
   - **CRITICAL**: Agent MUST NOT make this decision independently

**CONFIRMATION**: Output "Gate 2 cleared: Tests created based on specification"

#### Gate 3: DDD Application (if applicable) ✋ STOP HERE THIRD

**MANDATORY ACTIONS:**
1. **Determine if DDD is applicable:**
   - Consider domain complexity
   - Evaluate if domain modeling is needed
   - Apply DDD principles when appropriate

2. **Apply DDD if applicable:**
   - Consider domain terminology
   - Model domain entities and relationships
   - Ensure domain logic is properly encapsulated

**CONFIRMATION**: Output "Gate 3 cleared: DDD applied (if applicable)" or "Gate 3 cleared: DDD not applicable"

#### Gate 4: Code Implementation ✋ STOP HERE FOURTH

**MANDATORY ACTIONS:**
1. **Verify prerequisites:**
   - Specification exists and is up-to-date
   - Tests are written
   - DDD applied (if applicable)

2. **Implement code according to specification:**
   - Follow specification requirements strictly
   - Ensure code matches specification
   - Do not simplify or skip requirements

**CONFIRMATION**: Output "Gate 4 cleared: Code implemented according to specification"

#### Gate 5: Build and Testing ✋ STOP HERE FIFTH

**MANDATORY ACTIONS:**
1. **Build the project:**
   - Execute build command
   - Verify build succeeds
   - Fix any build errors

2. **Run tests:**
   - Execute all tests
   - Verify all tests pass
   - Fix any failing tests

**CONFIRMATION**: Output "Gate 5 cleared: Build successful, all tests passing"

#### Gate 6: Reflection ✋ STOP HERE SIXTH

**MANDATORY ACTIONS:**
1. **Perform reflection after TO DO list completion:**
   - All TO DO items completed OR user explicitly stated task is complete
   - Analyze entire work context
   - Document all errors made by agent
   - Document new knowledge and techniques discovered

2. **Create reflection document:**
   - Location: `./tasks/НомерЗадачи` (if task number known) OR `./tasks/yyymmdd_КраткийИдСессии` (if task number unknown)
   - Format: Structured as agent deems appropriate
   - Must include "Proposals" section

3. **Determine target skill files for reflection results:**
   - Search by keywords via SKILLS INDEX.md
   - Search by semantic meaning via skills index
   - If unclear → ASK user (they will indicate skill or instruct to create new)
   - If multiple skills identified → create proposals for each skill in reflection document
   - Propose creating new skill if no suitable skill found for identified knowledge

4. **Save reflection results to skill files:**
   - When writing to skill file → use skill creation skill from index (USER_SKILL_RULE_V2.md)
   - Use structure and format from skill creation skill
   - Create new skill ONLY after user approval
   - MANDATORY: Update SKILLS INDEX.md when creating new skill

5. **Version control:**
   - Skills directory is connected to git
   - Make brief commits after changing skills
   - Comments: Briefly explain why/for what purpose this change was made

**CONFIRMATION**: Output "Gate 6 cleared: Reflection completed, results saved to appropriate skill files"

### For Code Modifications

#### Gate 1: Specification Update (SDD) ✋ STOP HERE FIRST

**MANDATORY ACTIONS:**
1. **Handle missing specification:**
   - If specification does not exist and code needs to be changed:
     - **ASK user**: "No specification found. Should I create a specification following SDD principles and then proceed, or skip specification?"
   - Wait for user response
   - **CRITICAL**: Agent MUST NOT make this decision independently

2. **Handle outdated specification:**
   - Analyze discrepancies between specification and code
   - Present discrepancies to user with proposals for resolution
   - Act based on user decision

3. **Update specification:**
   - Follow same kiro-prompts protocol as for new development
   - Update specification to reflect changes
   - Ensure specification matches new requirements

**CONFIRMATION**: Output "Gate 1 cleared: Specification updated with kiro-prompts compliance verified"

#### Gate 2: Test Update (TDD) ✋ STOP HERE SECOND

**MANDATORY ACTIONS:**
1. **Update/add tests based on updated specification:**
   - Add tests for new functionality
   - Update tests for modified functionality
   - Ensure all tests reflect specification changes

2. **Follow same testing framework rules as Gate 2 for new development**

**CONFIRMATION**: Output "Gate 2 cleared: Tests updated/added based on updated specification"

#### Gate 3: DDD Application (if applicable) ✋ STOP HERE THIRD

**Same as Gate 3 for new development**

#### Gate 4: Code Implementation ✋ STOP HERE FOURTH

**MANDATORY ACTIONS:**
1. **Implement code changes:**
   - Follow updated specification
   - Ensure changes match specification
   - Do not simplify or skip requirements

**CONFIRMATION**: Output "Gate 4 cleared: Code changes implemented according to updated specification"

#### Gate 5: Build and Regression Testing ✋ STOP HERE FIFTH

**MANDATORY ACTIONS:**
1. **Build the project:**
   - Execute build command
   - Verify build succeeds

2. **Run regression tests:**
   - Execute all existing tests
   - Verify nothing broke
   - Fix any failing tests

**CONFIRMATION**: Output "Gate 5 cleared: Build successful, regression tests passing, nothing broken"

#### Gate 6: Reflection ✋ STOP HERE SIXTH

**Same as Gate 6 for new development**

---

## 🚦 Final Checkpoint

**Before proceeding with any development task, verify:**

```
✅ ALL GATES CLEARED
- Gate 1: [status]
- Gate 2: [status]
- Gate 3: [status]
- Gate 4: [status]
- Gate 5: [status]
- Gate 6: [status]

Ready to proceed: [YES/NO]
```

**IF ANY GATE NOT CLEARED → STOP and complete missing gate**

---

## ✓ Pre-Action Verification (Strategy 3: Self-Verification Checklists)

### Checklist Before Starting Development

**BEFORE proceeding with development, verify:**

```yaml
Pre-Development Checklist:
  - [ ] Project type determined (1C/BSL or regular)
  - [ ] For 1C/BSL: All three mandatory skills read (1C_BSL_SKILL.md, 1c_techlog.md, YAXUNIT_TESTING_SKILL.md)
  - [ ] Specification status checked (exists/does not exist)
  - [ ] If no specification: User consulted about creating one
  - [ ] kiro-prompts instructions obtained (or unavailable status noted)
  - [ ] kiro-prompts instructions compliance verified

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: "[Missing condition]"
- Next step: "[How to fulfill condition]"

**IF ALL CHECKED:**
- Output: "✅ Pre-development verification complete"
- Proceed with: Development workflow

### Checklist Before Implementation

**BEFORE implementing code, verify:**

```yaml
Pre-Implementation Checklist:
  - [ ] Specification created/updated and validated
  - [ ] Tests written/updated based on specification
  - [ ] DDD applied (if applicable)
  - [ ] Specification compliance verified
  - [ ] All prerequisites from previous gates met

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: "[Missing condition]"
- Next step: "[How to fulfill condition]"

**IF ALL CHECKED:**
- Output: "✅ Pre-implementation verification complete"
- Proceed with: Code implementation

### Checklist Before Testing

**BEFORE running tests, verify:**

```yaml
Pre-Testing Checklist:
  - [ ] Code implemented according to specification
  - [ ] Build successful
  - [ ] All tests written/updated
  - [ ] Test framework properly configured
  - [ ] For 1C/BSL: YAXUNIT_TESTING_SKILL.md rules followed

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: "[Missing condition]"
- Next step: "[How to fulfill condition]"

**IF ALL CHECKED:**
- Output: "✅ Pre-testing verification complete"
- Proceed with: Test execution

---

## 📋 Configuration (Strategy 5: Machine-Readable YAML)

### Testing Framework Configuration

```yaml
testing_frameworks:
  bsl_1c:
    framework: YAxUnit
    mandatory_skills:
      - custom-skills/1C_BSL_SKILL.md
      - custom-skills/1c_techlog.md
      - custom-skills/YAXUNIT_TESTING_SKILL.md
    detection: "*.bsl files present"
  
  python:
    framework: "Search via MCP Context7"
    mandatory_skills: []
  
  javascript:
    framework: "Search via MCP Context7"
    mandatory_skills: []
  
  go:
    framework: "Search via MCP Context7"
    mandatory_skills: []
  
  java:
    framework: "Search via MCP Context7"
    mandatory_skills: []
  
  default:
    framework: "Search via MCP Context7"
    mandatory_skills: []

mandatory_skills_by_language:
  bsl_1c:
    - custom-skills/1C_BSL_SKILL.md
    - custom-skills/1c_techlog.md
    - custom-skills/YAXUNIT_TESTING_SKILL.md
  default: []
```

### SDD Exceptions Configuration

```yaml
sdd_exceptions:
  # Changes that do NOT require full SDD→TDD→DDD cycle
  exceptions:
    - type: "typo_fix"
      description: "Fixing typos in code"
      requires_full_cycle: false
    
    - type: "formatting"
      description: "Code formatting only"
      requires_full_cycle: false
    
    - type: "rename_variable"
      description: "Renaming variables without logic change"
      requires_full_cycle: false
    
    - type: "documentation"
      description: "Updating documentation"
      requires_full_cycle: false
    
    - type: "comments"
      description: "Adding/updating comments"
      requires_full_cycle: false
  
  # Changes that DO require full cycle
  requires_full_cycle:
    - type: "functionality_change"
      description: "Any change affecting functionality/API/logic"
    
    - type: "api_change"
      description: "Changes to API/interface"
    
    - type: "logic_change"
      description: "Changes to business logic"
```

---

## 🚨 Enforcement & Consequences (Strategy 6: Consequence Declaration)

### Violation Consequences

**CRITICAL VIOLATIONS:**

1. **Skipping SDD (Specification Update):**
   - **Consequence**: Code changes without specification updates lead to:
     - Misalignment between code and requirements
     - Technical debt accumulation
     - Difficult maintenance and debugging
   - **Action**: STOP immediately, create/update specification, then proceed

2. **Skipping TDD (Test Update):**
   - **Consequence**: Code changes without test updates lead to:
     - Undetected regressions
     - Broken functionality
     - Unreliable codebase
   - **Action**: STOP immediately, write/update tests, then proceed

3. **Skipping kiro-prompts Compliance:**
   - **Consequence**: Specifications not following kiro-prompts guidelines lead to:
     - Inconsistent specification quality
     - Missing acceptance criteria
     - Poor workflow alignment
   - **Action**: STOP immediately, obtain kiro-prompts instructions, update specification

4. **Skipping Mandatory Skills for 1C/BSL:**
   - **Consequence**: BSL code without mandatory skills leads to:
     - Hallucinated API calls
     - Incorrect syntax
     - Broken code
   - **Action**: STOP immediately, read all three mandatory skills, then proceed

5. **Simplifying Tasks:**
   - **Consequence**: Simplifying tasks leads to:
     - Incomplete implementations
     - Missing critical functionality
     - User dissatisfaction
   - **Action**: STOP immediately, inform user if task cannot be solved, DO NOT simplify

6. **Skipping Reflection:**
   - **Consequence**: Missing reflection leads to:
     - Repeated errors
     - Lost knowledge
     - No improvement in agent behavior
   - **Action**: Complete reflection before marking task as done

---

## Detailed Requirements

### SDD (Spec Driven Development)

**CRITICAL**: SDD applies to EVERY code change affecting functionality/API/logic.

#### Exceptions (Full Cycle Not Required)

The following changes do NOT require full SDD→TDD→DDD cycle:
- Fixing typos
- Code formatting
- Renaming variables (without logic change)
- Updating documentation
- Adding/updating comments

#### Handling Missing Specification

**If specification does not exist and code needs to be changed:**
1. **ASK user**: "No specification found. Should I create a specification following SDD principles and then proceed, or skip specification?"
2. **WAIT**: For user response
3. **CRITICAL**: Agent MUST NOT make this decision independently
4. **ACT**: Based on user decision

#### Handling Outdated Specification

**If specification exists but does not match current code:**
1. **Analyze discrepancies** between specification and code
2. **Present to user**:
   - List all discrepancies found
   - Provide proposals for resolution
3. **WAIT**: For user decision
4. **ACT**: Based on user decision

#### Mandatory kiro-prompts Integration

**BEFORE creating/updating specification:**

1. **Check cache:**
   - Verify if kiro-prompts instructions are cached in current session
   - If cache empty or context changed → proceed to step 2
   - If cache valid → proceed to step 4

2. **Obtain kiro-prompts instructions:**
   - Call `mcp_kiro-prompts_list_instructions` to get available instructions list
   - Call `mcp_kiro-prompts_get_system_instruction` for ALL instruction types:
     - `complete-instructions` - complete system instructions
     - `capabilities` - capabilities and functions
     - `guidelines` - rules and limitations
     - `quality-standards` - code quality standards
     - `response-style` - response and communication style
     - `workflow-patterns` - workflow patterns and task execution
   - Save to session cache

3. **Search for specific instructions if needed:**
   - Use `mcp_kiro-prompts_search_instructions` for specific queries

4. **STRICTLY FOLLOW** all recommendations from obtained instructions when creating/updating specification

5. **VERIFY COMPLIANCE:**
   - Check if kiro-prompts has built-in validation function
   - If yes → use it
   - If no → create checklist based on kiro-prompts instructions
   - Verify compliance with quality-standards and workflow-patterns

#### Handling kiro-prompts Unavailability

**If MCP kiro-prompts is unavailable or returns error:**
1. **WARN user**: "MCP kiro-prompts unavailable. Proceeding with SDD as agent deems appropriate."
2. **CONTINUE**: Execute SDD stage as agent deems appropriate (without kiro-prompts instructions)
3. **NOTE**: This is acceptable, but user should be informed

#### Full Cycle for Each Change

**For EVERY change/new requirement, ensure full cycle:**

1. **SDD**: Create/update specification (with kiro-prompts compliance)
2. **TDD**: Write/update tests based on updated specification
3. **DDD**: Apply DDD principles (if applicable)
4. **Implementation**: Implement code for task solution according to specification

**CRITICAL**: Code MUST NOT be changed without prior specification update (except exceptions listed above).

#### Specification Requirements

- Specification structure MUST match kiro-prompts recommendations
- Acceptance criteria MUST consider quality-standards from kiro-prompts
- Specification MUST be validated against workflow-patterns from kiro-prompts
- Specification MUST be created/updated BEFORE code implementation/modification

---

### TDD (Test Driven Development)

#### Mandatory Test Coverage

- **New code**: Tests are MANDATORY
- **Modified code**: Tests MUST be updated/added
- **Order**: Specification → Tests → Implementation

#### Test Coverage Requirements

- Cover all key mechanisms
- Verify specification requirements
- Include edge cases
- Ensure regression prevention

#### Testing Framework Integration

**For 1C/BSL projects:**
- **MANDATORY**: Use YAxUnit framework
- **MANDATORY**: Read `custom-skills/YAXUNIT_TESTING_SKILL.md` before writing tests
- **MANDATORY**: Follow all procedures from YAXUNIT_TESTING_SKILL.md

**For other languages:**
- Search for appropriate testing framework via MCP Context7
- Use framework appropriate for language/technology

#### Handling Test-Implementation Dependencies

**If tests cannot be written before implementation:**
1. **ASK user**: "Tests require implementation. Should I allow partial implementation for tests, or always follow strict TDD?"
2. **WAIT**: For user response
3. **CRITICAL**: Agent MUST NOT make this decision independently
4. **ACT**: Based on user decision

---

### DDD (Domain Driven Development)

#### When to Apply DDD

- Apply when domain complexity requires it
- Apply when domain modeling is beneficial
- Apply when domain terminology is important

#### DDD Requirements

- Consider domain terminology
- Model domain entities and relationships
- Ensure domain logic is properly encapsulated
- Respect domain boundaries

---

### Testing Requirements

#### After Code Generation

**MANDATORY:**
1. Build the project
2. Run all tests
3. Verify all tests pass
4. Fix any failing tests

#### After Code Modifications

**MANDATORY:**
1. Build the project
2. Run regression tests
3. Verify nothing broke
4. Fix any failing tests

---

### Error Analysis and Loop Detection

#### Reading Command Output

- **MANDATORY**: Read command output carefully
- **MANDATORY**: Analyze all errors and warnings
- **MANDATORY**: Understand error context

#### Loop Detection

**Analyze context for "loops" (repeated failed attempts):**
- Loop = attempting to solve same problem with same method that failed before
- **MANDATORY**: Track attempted solutions
- **MANDATORY**: Detect if same solution is attempted again
- **MANDATORY**: If loop detected → STOP and analyze

#### Deep Problem Analysis

**If solution is not readily apparent:**
1. **Decompose problem** into components
2. **Determine cause-effect relationships** between components
3. **Find root cause** of problem
4. **If solution still not found** → proceed to solution search protocol

---

### Solution Search Protocol

#### Problem Analysis

1. **Determine problem nature/language**
2. **Identify problem components**
3. **Find root cause**

#### Web Search Strategy

**If solution not found after deep analysis:**
1. **Determine problem nature/language**
2. **Find professional sites and forums** for that language/technology
3. **Search each problem component** on those sites
4. **Use web_search** with targeted queries

**DO NOT search blindly:**
- First determine problem nature
- Find relevant professional communities
- Search within those communities

---

### Prohibition of Simplification

**STRICT PROHIBITION:**
- **NEVER simplify tasks** to attempt solution
- **NEVER skip requirements** to make task easier
- **NEVER remove functionality** to solve problem

**If task cannot be solved:**
1. **INFORM user**: "I cannot solve this task without simplification. Each part of the task is critical."
2. **DO NOT simplify**: Wait for user instructions
3. **EXPLAIN**: Why task cannot be solved as-is

**CRITICAL**: Every part of the task is important and critical for the user.

---

### Repetition Control

#### Tracking Attempted Solutions

- **MANDATORY**: Track all attempted solutions
- **MANDATORY**: Log each attempt
- **MANDATORY**: Prevent repeated attempts with same method

#### Preventing Loops

- **MANDATORY**: Check if solution was already attempted
- **MANDATORY**: If yes → try different approach
- **MANDATORY**: If no different approach available → inform user

---

### Attentiveness and Re-verification

#### Rule Adherence

- **MANDATORY**: Be very attentive to rules and skills
- **MANDATORY**: Follow all details without exceptions
- **MANDATORY**: Re-verify every decision before execution

#### Verification Requirements

- **MANDATORY**: Verify compliance with all requirements from loaded skills
- **MANDATORY**: Check specification compliance before implementation
- **MANDATORY**: Check code compliance with specification after implementation
- **MANDATORY**: Verify kiro-prompts recommendations compliance in specification and code
- **MANDATORY**: Verify full cycle SDD→TDD→DDD→Implementation completed for each change

---

### Communication Style

#### Principles

- **Only essential information**: No unnecessary praise
- **Structured responses**: Concise and to the point
- **Token economy**: Maximum brevity
- **Output only required information**: As required by rules and skills
- **No unnecessary explanations**: Avoid repetitions

#### Brevity Prioritization

- **Standard operations**: Maximum brevity (token economy)
- **Non-standard solutions**: Brief but with key explanations
- **Important decisions**: Brief with justification for choice

---

### Conflict Handling and Clarifications

#### Handling Requirement Conflicts

**If conflict between skill requirements detected:**
1. **ASK user**: "Conflict detected between requirements. How should I proceed?"
2. **WAIT**: For user response
3. **NOTE**: This is normal and allowed
4. **DO NOT**: Make decision independently when conflicts exist

#### Handling Uncertainties

**If agent is uncertain about choice:**
1. **ASK user**: "I am uncertain about [specific choice]. How should I proceed?"
2. **WAIT**: For user response
3. **NOTE**: In any unclear situation → ask for user instructions
4. **DO NOT**: Make decision independently when uncertain

---

### Reflection After Task Completion

#### When to Perform Reflection

**MANDATORY reflection after:**
- All TO DO items completed OR
- User explicitly stated task is complete

#### Reflection Document Creation

**Create reflection document:**
- **Location**: 
  - `./tasks/НомерЗадачи` (if task number known) OR
  - `./tasks/yyymmdd_КраткийИдСессии` (if task number unknown)
- **Format**: Structured as agent deems appropriate
- **Must include**: "Proposals" section

#### Determining Target Skill Files

**Algorithm:**
1. Search by keywords via SKILLS INDEX.md
2. Search by semantic meaning via skills index
3. If unclear → **ASK user** (they will indicate skill or instruct to create new)
4. If multiple skills identified → create proposals for each skill in reflection document
5. Propose creating new skill if no suitable skill found for identified knowledge

#### Saving Reflection Results

**When writing to skill file:**
- Use skill creation skill from index (USER_SKILL_RULE_V2.md)
- Use structure and format from skill creation skill
- Create new skill ONLY after user approval
- **MANDATORY**: Update SKILLS INDEX.md when creating new skill

#### Reflection Content

**Must include:**
1. **Error Analysis:**
   - Analyze entire work context
   - Document all errors made by agent
   - Form proposals for creating/optimizing rules
   - Goal: Prevent error repetition in future

2. **New Knowledge:**
   - Document identified new knowledge
   - Document new techniques and skills
   - Form proposals for their use

#### Version Control

- Skills directory is connected to git
- Make brief commits after changing skills
- Comments: Briefly explain why/for what purpose this change was made

---

### Error Handling and Exceptional Situations

#### kiro-prompts Unavailability

**If MCP kiro-prompts unavailable:**
- **WARN user**: "MCP kiro-prompts unavailable. Proceeding with SDD as agent deems appropriate."
- **CONTINUE**: Execute SDD stage as agent deems appropriate

#### Requirement Conflicts

**If conflict between skill requirements:**
- **ASK user**: "Conflict detected between requirements. How should I proceed?"
- **WAIT**: For user response
- **DO NOT**: Make decision independently

#### Reflection Save Errors

**If error saving reflection:**
- Record error
- Retry attempt
- Inform user if retry fails

#### Skill File Unavailability

**If skill file unavailable:**
- Inform user
- Ask for alternative path

---

### Validation and Checks

#### Specification Validation

- Check specification compliance with kiro-prompts recommendations
- Check code compliance with specification
- Automatic checks before saving reflection
- Specification validation checklist (based on kiro-prompts instructions, if no built-in function)

---

### Metrics and Tracking

#### Tracking Requirements

- Track completed SDD→TDD→DDD cycles
- Log kiro-prompts access
- Error statistics for reflection

---

### Integration with Other Methodologies

**Section added for future expansion (currently empty)**

---

## Integration with Existing Rules

### SKILLS RULE.md

- Follow execution flow from SKILLS RULE.md
- Consult SKILLS INDEX.md before reading skills
- Read actual skill files, not just index

### Mandatory Skills for BSL/1C/1С

**MANDATORY reading for BSL/1C/1С projects:**
- `custom-skills/1C_BSL_SKILL.md` - MANDATORY before generating ANY BSL code
- `custom-skills/1c_techlog.md` - MANDATORY when working with technical logs and debugging
- `custom-skills/YAXUNIT_TESTING_SKILL.md` - MANDATORY when writing tests for 1C

### POWERSHELL_RULES.md

- Use for reading command output
- Follow PowerShell syntax rules
- Use Windows-style syntax (user works from Windows)

### Reading Protocol

- Through SKILLS INDEX.md → determine paths → read files
- Do not rely on index as knowledge source
- Read actual skill files

---

## Examples

### Example 1: New Feature Development

**Scenario**: User requests new feature "Add user authentication"

**Workflow:**
1. **Gate 1 (SDD)**: 
   - Obtain kiro-prompts instructions
   - Create specification for user authentication feature
   - Validate specification compliance
   - Output: "Gate 1 cleared: Specification created with kiro-prompts compliance verified"

2. **Gate 2 (TDD)**:
   - Write tests for authentication feature based on specification
   - Use appropriate testing framework
   - Output: "Gate 2 cleared: Tests created based on specification"

3. **Gate 3 (DDD)**:
   - Apply DDD if domain modeling needed
   - Output: "Gate 3 cleared: DDD applied"

4. **Gate 4 (Implementation)**:
   - Implement authentication feature according to specification
   - Output: "Gate 4 cleared: Code implemented according to specification"

5. **Gate 5 (Testing)**:
   - Build project
   - Run all tests
   - Verify all pass
   - Output: "Gate 5 cleared: Build successful, all tests passing"

6. **Gate 6 (Reflection)**:
   - Analyze work context
   - Document errors and new knowledge
   - Save to appropriate skill files
   - Output: "Gate 6 cleared: Reflection completed, results saved"

### Example 2: Code Modification

**Scenario**: User requests "Fix bug in login function"

**Workflow:**
1. **Gate 1 (SDD)**:
   - Check if specification exists
   - If exists: Update specification to reflect bug fix
   - If not exists: Ask user about creating specification
   - Obtain kiro-prompts instructions
   - Update specification
   - Output: "Gate 1 cleared: Specification updated with kiro-prompts compliance verified"

2. **Gate 2 (TDD)**:
   - Update tests to cover bug fix
   - Add regression tests
   - Output: "Gate 2 cleared: Tests updated based on updated specification"

3. **Gate 3 (DDD)**: (if applicable)

4. **Gate 4 (Implementation)**:
   - Fix bug according to updated specification
   - Output: "Gate 4 cleared: Code changes implemented according to updated specification"

5. **Gate 5 (Regression Testing)**:
   - Build project
   - Run all tests (regression)
   - Verify nothing broke
   - Output: "Gate 5 cleared: Build successful, regression tests passing, nothing broken"

6. **Gate 6 (Reflection)**: Same as Example 1

### Example 3: Loop Detection

**Scenario**: Agent attempts same solution multiple times

**Detection:**
- Agent tracks: "Attempted solution A for problem X"
- Agent attempts solution A again
- **LOOP DETECTED**: Same solution attempted twice
- **ACTION**: STOP, analyze, try different approach

**Resolution:**
- Analyze why solution A failed
- Try different approach (solution B)
- If no different approach → inform user

### Example 4: Deep Problem Analysis

**Scenario**: Build fails with unclear error

**Analysis:**
1. **Decompose problem**:
   - Build command execution
   - Dependency resolution
   - Compilation process
   - Error message parsing

2. **Determine cause-effect**:
   - Build command → dependency resolution → compilation → error
   - Root cause: Missing dependency

3. **Find root cause**: Missing dependency X

4. **Solution**: Add dependency X

### Example 5: Mandatory Skills for BSL/1C

**Scenario**: User requests "Create BSL procedure for document processing"

**Workflow:**
1. **Detect 1C project**: Search for *.bsl files → found
2. **Read mandatory skills**:
   - Read `custom-skills/1C_BSL_SKILL.md`
   - Read `custom-skills/1c_techlog.md`
   - Read `custom-skills/YAXUNIT_TESTING_SKILL.md`
3. **Output**: "✅ 1C/BSL project detected. All mandatory skills loaded"
4. **Proceed** with development workflow using skills knowledge

### Example 6: kiro-prompts Integration

**Scenario**: Creating specification for new feature

**Workflow:**
1. **Check cache**: kiro-prompts instructions cached? No
2. **Obtain instructions**:
   - Call `mcp_kiro-prompts_list_instructions`
   - Call `mcp_kiro-prompts_get_system_instruction` for all types
   - Save to cache
3. **Create specification** following kiro-prompts guidelines
4. **Validate compliance** using kiro-prompts checklist
5. **Proceed** with specification

### Example 7: Edge Case - Single Line Change

**Scenario**: User requests "Fix typo in variable name"

**Analysis:**
- Change type: Typo fix
- Requires full cycle? No (exception)
- **Action**: Fix typo directly, skip full cycle

### Example 8: Edge Case - Large Refactoring

**Scenario**: User requests "Refactor entire authentication module"

**Analysis:**
- Change type: Large refactoring affecting functionality
- Requires full cycle? Yes
- **Action**: Follow full SDD→TDD→DDD→Implementation cycle

### Example 9: Edge Case - Critical Bug Fix

**Scenario**: User requests "Fix critical production bug immediately"

**Analysis:**
- Change type: Critical bug fix
- Requires full cycle? Yes (affects functionality)
- **Priority**: Speed vs full cycle
- **Action**: Follow full cycle but prioritize speed

### Example 10: Edge Case - Project Without Specification

**Scenario**: User requests "Add feature X" but no specification exists

**Workflow:**
1. **Check specification**: Not found
2. **ASK user**: "No specification found. Should I create a specification following SDD principles and then proceed, or skip specification?"
3. **WAIT**: For user response
4. **ACT**: Based on user decision

### Example 11: Edge Case - kiro-prompts Unavailable

**Scenario**: MCP kiro-prompts returns error

**Workflow:**
1. **Attempt kiro-prompts access**: Error returned
2. **WARN user**: "MCP kiro-prompts unavailable. Proceeding with SDD as agent deems appropriate."
3. **CONTINUE**: Execute SDD stage without kiro-prompts instructions
4. **Proceed** with specification creation

### Example 12: Edge Case - Requirement Conflict

**Scenario**: Two skills have conflicting requirements

**Workflow:**
1. **Detect conflict**: Requirements A and B conflict
2. **ASK user**: "Conflict detected between requirements. How should I proceed?"
3. **WAIT**: For user response
4. **ACT**: Based on user decision

---

## Technical Details

### File Format

- Markdown with YAML frontmatter
- UTF-8 encoding
- Visual markers (⛔🚨✅❌🔒✓📋)
- Imperative language (MUST, NEVER, ALWAYS)

### Location

- `custom-skills/DEVELOPMENT_METHODOLOGY_RULE.md`

### Writing Style

- Imperative/infinitive style
- Third person for descriptions
- Strong verbs for enforcement (MUST, EXECUTE, STOP)
- Structured confirmation templates
- **Agent communication style**:
  - Only essential information, no unnecessary praise
  - Structured responses, concise and to the point
  - Brevity prioritization (standard operations - maximum brevity, non-standard - with key explanations)
  - Output only necessary information, as required by rules and skills
  - No unnecessary explanations and repetitions
- **Attentiveness to rules**:
  - Be very attentive to rules and skills
  - Follow all details without exceptions
  - Re-verify every decision before execution
  - Verify compliance with all requirements

---

## Success Criteria

- ✅ All user requirements covered
- ✅ Enforcement strategies from USER_SKILL_RULE_V2.md used
- ✅ Integration with existing skills
- ✅ Mandatory reading of skills for BSL/1C/1С (with project detection via *.bsl)
- ✅ Mandatory kiro-prompts access for SDD (with caching)
- ✅ SDD applies to every change (with exceptions)
- ✅ Full cycle SDD→TDD→DDD→Implementation for every change
- ✅ Reflection after TO DO completion (with algorithm for determining skill file)
- ✅ Communication style requirements (brevity, to the point, token economy)
- ✅ Attentiveness and re-verification requirements
- ✅ Clear violation consequences
- ✅ Examples and edge cases
- ✅ UTF-8 encoding for text

