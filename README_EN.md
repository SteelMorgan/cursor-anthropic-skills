# Skills Collection for Cursor IDE

**[🇺🇸 English](README_EN.md) | [🇷🇺 Русский](README.md)**

A skills collection for Cursor IDE, based on open sources, particularly Claude Code Templates. The framework ensures automatic application of specialized knowledge by AI agents when working with various technologies and domains.

## Problem and Solution

### Problem

Cursor does not support working with multiple agents simultaneously. This limits the ability to use specialized knowledge embedded in various agents.

### Solution

A prompt mechanism (user rules) has been developed that allows extracting "knowledge" from agents and converting it into skills. When receiving a request from a user, the agent:

1. Analyzes the request for keywords and semantic meaning
2. Consults the skills index (`SKILLS INDEX.md`)
3. Selects appropriate skills based on keywords and semantic search
4. Loads and applies knowledge from the found skills
5. Proceeds with the request considering best practices and specialized knowledge

This allows the agent to consider best practices and possess information about specific technologies, even if this knowledge was not initially in its context.

## Quick Start

### A. Clone the Repository

```powershell
git clone <repository-url>
cd "YOUR_PATH" (replace path with yours if desired)
```

### B. Update Path in SKILLS RULE.md

In the file `./SKILLS RULE.md`, in the **STEP 2: CONSULT SKILLS INDEX** section, specify your project path:

```markdown
### STEP 2: CONSULT SKILLS INDEX
**MANDATORY ACTIONS:**
1. ✅ Read `YOUR_PATH\SKILLS INDEX.md` file
```

Replace `D:\My Projects\FrameWork Global\LLM Skills\` with your project path.

### C. Update Paths in SKILLS INDEX.md

Perform a similar path replacement in the file `./SKILLS INDEX.md`.

**Important:** You can use relative paths, but practice has shown that the agent starts working unstable and finds files intermittently. It is recommended to use global find-and-replace (Ctrl + H) once to change the project path to yours in all occurrences.

### D. Add Rule to Cursor

The text from the file `SKILLS RULE.md` must be added to Cursor IDE as a rule:

1. Open the file `SKILLS RULE.md`
2. Copy all its contents
3. In Cursor, go to Settings → Rules → User Rules
4. Add the copied text as a new rule

**Note:** You can simply place the file in the user directory, but for me it is not recognized from there. Adding manually through the Cursor interface guarantees it will work.

### E. Usage

Use the agent as usual. It will automatically load the necessary skills based on your context. If the agent still hasn't loaded the needed skill — simply tell it that it needs to load a skill about something. It will find it if such a skill exists in the index.

## Key Features

- **Skill search based on semantic analysis of user request** — the system understands user intent and selects relevant skills
- **Skill search by keywords from user request** — quick identification of the needed skill by technical terms
- **Use of "protection, enhancement, and control" mechanics in prompts** — application of 6 control strategies to increase agent compliance with skill rules

## Project Structure

```
D:\My Projects\FrameWork Global\LLM Skills\
├── SKILLS INDEX.md                   # Main skills index (map of paths to skills)
├── SKILLS RULE.md                    # Global application rule (add to Cursor!)
├── README.md                         # Project documentation (Russian)
├── README_EN.md                      # Project documentation (English)
├── CHANGELOG.md                      # Changelog
├── CONTRIBUTING.md                   # Contributor guide
├── THIRD_PARTY_NOTICES.md            # Third-party software notices
├── .gitignore                        # Excludes third-party skill repositories
│
├── custom-skills\                    # Project-specific custom skills
│   ├── POWERSHELL_RULES.md          # PowerShell rules
│   ├── DOCKER_SKILLS.md             # Docker operations
│   ├── 1C_BSL_SKILL.md              # 1C/BSL development
│   ├── 1c_techlog.md                 # 1C technical logging
│   ├── YAXUNIT_TESTING_SKILL.md     # YAxUnit testing
│   ├── DEVELOPMENT_METHODOLOGY_RULE.md # SDD/TDD/DDD methodology
│   ├── GO_SKILL.md                  # Go language
│   ├── MERMAID_SKILL.md             # Mermaid diagrams
│   ├── USER_SKILL_RULE_V2.md        # Skill creation guide
│   └── claude-agent-skills\         # Claude Agent Skills collection (140+ skills)
│       ├── ai-specialists\           # AI specialists (9 skills)
│       ├── development-team\         # Development team (8 skills)
│       ├── development-tools\        # Development tools (12 skills)
│       ├── database\                 # Databases (8 skills)
│       ├── security\                 # Security (6 skills)
│       ├── programming-languages\    # Programming languages (11 skills)
│       └── ...                       # And much more
│
├── anthropics-skills\                # Clone of https://github.com/anthropics/skills
│   ├── artifacts-builder\           # Complex HTML artifacts with React/Tailwind
│   ├── playwright-docker-automation\ # Browser automation in Docker
│   ├── document-skills\             # Document creation (docx, pdf, xlsx, pptx)
│   ├── skill-creator\                # Skill creation guide
│   ├── template-skill\              # Basic skill template
│   └── ...                          # Other official Anthropic skills
│
└── claude-code-templates\            # Clone of https://github.com/davila7/claude-code-templates
    └── cli-tool\components\skills\   # Extended Claude Code skills
```

## Available Skills

### Custom Project Skills (~9 skills, some are in debugging and testing stage)

- **PowerShell Scripts** — PowerShell command generation for Windows
- **Docker Operations** — Docker container and service management
- **1C/BSL Development** — 1C:Enterprise development with BSL validation
- **YAxUnit Testing** — Writing unit tests for 1C using YAxUnit
- **Go Language** — Go language development
- **Mermaid Diagrams** — Mermaid diagram creation
- **Development Methodology** — SDD/TDD/DDD development methodology for 1C/BSL projects
- **Enhanced Skill Creator** — Creating reliable skills with built-in enforcement (6 strategies)
- **1C Technical Logging** — 1C technical log analysis

### Official Anthropic Skills (~14 skills)

#### Creative & Design (4 skills)
- Algorithmic Art, Canvas Design, Slack GIF Creator, Theme Factory

#### Development & Technical (3 skills)
- Artifacts Builder, MCP Builder, Web App Testing

#### Document Skills (4 skills)
- DOCX, PDF, PPTX, XLSX

#### Enterprise & Communication (2 skills)
- Brand Guidelines, Internal Communications

#### Meta (1 skill)
- Template Skill

### Claude Code Skills (~19 skills)

#### Unique Extensions (5 skills)
- Git Commit Helper, Email Composer, Excel Analysis, PDF Processing, PDF Processing Pro

#### Mirrored Anthropic Skills (14 skills)
- Duplicates of official Anthropic skills with additional capabilities

### Claude Agent Skills (~140 skills)

#### AI Specialists (9 skills)
- Prompt Engineering, LLMs.txt Maintainer, LLM Maintenance, Model Evaluation, Search Specialist, Search Specialization, Task Decomposition, AI Ethics, Hackathon Strategy

#### Development Team (8 skills)
- Backend Architecture, Frontend Development, Full-Stack Development, iOS Development, Mobile Development, DevOps Engineering, UI/UX Design, CLI UI Design

#### Development Tools (12 skills)
- Code Review, MCP Integration, Command Development, Context Management, Debugging, Developer Experience, Error Detection, Performance Profiling, Test Automation, Code Cleanup, Flutter/Go Review

#### Database (8 skills)
- Database Administration, Database Architecture, Database Optimization, Neon Auth, Neon Database Architecture, Neon Expert, Supabase Schema, NoSQL

#### MCP Dev Team (7 skills)
- MCP Server Architecture, MCP Deployment, MCP Integration, MCP Protocol, MCP Registry, MCP Security Audit, MCP Testing

#### Security (6 skills)
- Security Auditing, Security Auditing (Code), Penetration Testing, Incident Response, Compliance, API Security Audit

#### Documentation (4 skills)
- API Documentation, Technical Writing, Changelog Generation, Docusaurus

#### Expert Advisors (4 skills)
- Agent Development, Architecture Review, Dependency Management, Documentation Expertise

#### API & GraphQL (3 skills)
- GraphQL Architecture, GraphQL Performance, GraphQL Security

#### DevOps Infrastructure (8 skills)
- Cloud Architecture, Deployment Automation, DevOps Troubleshooting, Infrastructure Security, Monitoring, Network Engineering, Terraform, Vercel Deployment

#### Data & AI (8 skills)
- Data Engineering, Data Science, ML Engineering, AI Engineering, NLP Engineering, MLOps, Computer Vision, Quantitative Analysis

#### Blockchain & Web3 (3 skills)
- Smart Contract Development, Smart Contract Auditing, Web3 Integration

#### Git & Version Control (1 skill)
- Git Flow

#### Realtime (1 skill)
- Supabase Realtime

#### Modernization (3 skills)
- Architecture Modernization, Legacy Modernization, Cloud Migration

#### Game Development (4 skills)
- Unity Development, Unreal Development, Game Design, 3D Art

#### FFmpeg Clip Team (8 skills)
- Video Editing, Audio Mixing, Social Media Clips, Audio Quality, Podcast Transcription, Podcast Metadata, Timestamp Precision, Podcast Content Analysis

#### OCR Extraction Team (4 skills)
- Visual OCR, OCR Preprocessing, Document Structure Analysis, OCR Quality Assurance

#### Podcast Creator Team (2 skills)
- SEO Podcast Optimization, Podcast Editing

#### Obsidian Ops Team (3 skills)
- Metadata Management, Connection Management, Tag Taxonomy

#### Programming Languages (11 skills)
- Python, TypeScript, JavaScript, C#, C++, Rust, Go, PHP, SQL, Shell Scripting, C

#### Performance Testing (5 skills)
- Load Testing, Performance Engineering, React Performance, Web Vitals, Test Automation Setup

#### Web Tools (5 skills)
- Next.js Architecture, SEO Analysis, Web Accessibility, URL Validation, URL Extraction

#### Deep Research Team (12 skills)
- Research Coordination, Research Orchestration, Research Synthesis, Academic Research, Technical Research, Fact Checking, Data Analysis, Report Generation, Competitive Intelligence, Query Clarification, Research Brief Generation, Nia Oracle

#### Business & Marketing (9 skills)
- Business Analysis, Product Strategy, Content Marketing, Customer Support, Legal Advisory, Marketing Attribution, Payment Integration, Risk Management, Sales Automation

**Total: over 180 skills** available for various technologies and domains.

## Creating Skills

To create new skills, use the special skill `./custom-skills/USER_SKILL_RULE_V2.md`, which:

- Allows creating new skills using all 6 control strategies
- Knows that a new skill needs to be implemented in Skills Index (though it may sometimes forget)
- Uses "protection, enhancement, and control" mechanics to increase agent compliance with rules

### Skill Creation Process:

1. **Describe Requirements** — clearly describe what you want from the agent
2. **Check Understanding** — ask the agent if everything is clear, if there are any ambiguities or inconsistencies
3. **Create Skill** — ask the agent to create a skill based on `USER_SKILL_RULE_V2.md`
4. **Check Integration** — ensure the skill is added to `SKILLS INDEX.md` with correct keywords

## Testing

To verify the framework works:

1. **Describe a Task** — formulate a request that requires specialized knowledge
2. **Ask Agent to Report Skills Used** — ask the agent to report which skills it will use to complete the task
3. **Verify Application** — ensure the agent actually applied knowledge from the indicated skills

### Testing Example:

**Request:** "Write a PowerShell script to check Docker container status"

**Expected Agent Response:**
```
I read SKILLS INDEX.md and detected PowerShell and Docker keywords in the request.
Then I read the files:
- custom-skills/POWERSHELL_RULES.md
- custom-skills/DOCKER_SKILLS.md

Applied the following rules:
- Using ; instead of && for command separation
- Using Invoke-WebRequest instead of curl
- Correct Docker command syntax for PowerShell

Here's the script with correct syntax...
```

## Licenses

This project is open source and uses the following licenses:

- **LLM Skills Framework** — MIT License
- **Anthropic Skills Repository** — MIT License ([source](https://github.com/anthropics/skills))
- **Claude Code Templates** — MIT License ([source](https://github.com/davila7/claude-code-templates))

Detailed information about licenses and third-party software attributions is available in the `THIRD_PARTY_NOTICES.md` file.

---

**Note:** After cloning the repository, be sure to update paths in `SKILLS RULE.md` and `SKILLS INDEX.md` to your local paths, otherwise the system will not be able to find skill files.

