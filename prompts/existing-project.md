# Prompt: Add Context Mesh to Existing Project

Use this prompt when you have an existing project and want to add Context Mesh to it.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Let the AI analyze** your codebase
4. **Review** the generated context files
5. **Execute** - Use the execution prompt below if you want to continue building

---

## Prompt

```
I have an existing project and want to add Context Mesh to document and maintain context going forward.

Context Mesh is a simple framework with 3 steps:
1. Intent - Define what to build and why
2. Build - AI generates code, human supervises
3. Learn - Update context with learnings

Please analyze my current codebase and create a Context Mesh structure that documents what already exists.

Analyze:
1. Project structure (directories, files, configuration)
2. Technologies and frameworks used (package.json, requirements.txt, etc.)
3. Key features/modules in the codebase
4. Common patterns in the code
5. Technical decisions already made

Then create this folder structure:

context/
├── intent/
│   ├── project-intent.md (what the project does based on analysis)
│   └── feature-[name].md (one per identified feature/module)
├── decisions/
│   ├── 001-tech-stack.md (from package.json, etc.)
│   └── 002-[other-decisions].md (inferred from code)
├── knowledge/
│   ├── patterns/
│   │   └── [identified-pattern].md
│   └── anti-patterns/
├── agents/        # Optional: for reusable execution patterns
│   └── agent-*.md
└── evolution/
    └── changelog.md

Also create or update AGENTS.md file at project root following the template below.

Use these templates:

---
PROJECT-INTENT.MD TEMPLATE:
---
# Project Intent: [PROJECT_NAME]

## What
[What the project currently does - based on code analysis]

## Why
[Why this project exists - inferred from code/docs]

## Success Criteria
- [Inferred criterion 1]
- [Inferred criterion 2]

## Current Features
- [Feature 1 - identified from code]
- [Feature 2 - identified from code]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active
- **Note**: Generated from existing codebase analysis
---

---
FEATURE-[NAME].MD TEMPLATE:
---
# Feature: [FEATURE_NAME]

## What
[What this feature does - based on code analysis]

## Why
[Inferred purpose]

## Current Implementation
- [How it's currently implemented]

## Related
- Intent: project-intent.md
- Files: [list key files for this feature]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active
---

---
DECISIONS/001-TECH-STACK.MD TEMPLATE:
---
# Decision: Tech Stack

## Context
Existing project using established technologies.

## Decision
- Frontend: [detected from code]
- Backend: [detected from code]
- Database: [detected from code]
- Dependencies: [key dependencies]

## Rationale
[Inferred from code patterns and choices]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
- **Note**: Documented from existing implementation
---

---
PATTERNS/[PATTERN-NAME].MD TEMPLATE:
---
# Pattern: [PATTERN_NAME]

## Description
[What this pattern is]

## When to Use
[When to apply this pattern]

## Example
[Code example from the codebase]

## Status
- **Created**: [TODAY'S DATE]
- **Status**: Active
---

---
CHANGELOG.MD TEMPLATE:
---
# Changelog

## [Current State]

### Existing Features
- [Feature 1]
- [Feature 2]

### Tech Stack
- [Technology 1]
- [Technology 2]

---
*Context Mesh added: [TODAY'S DATE]*
*Note: This documents the existing state when Context Mesh was added*
---

---
AGENTS.MD TEMPLATE (create or update this file at project root):
---
# AGENTS.md

## Setup Commands

[From package.json, README, etc. - add install, dev, test, build commands]
Example:
- Install deps: `npm install`
- Start dev server: `npm run dev`
- Run tests: `npm test`
- Build: `npm run build`

## Code Style

[From codebase - add conventions, formatting rules]
Example:
- TypeScript strict mode
- Single quotes, no semicolons
- Follow patterns from `@context/knowledge/patterns/`

## Context Files to Load

**This is the key integration point with Context Mesh.**

When working on this project, AI agents should load Context Mesh files for strategic context:

### Project Overview
- @context/intent/project-intent.md - Overall project goals and scope

### Technical Decisions
- @context/decisions/001-tech-stack.md - Technology stack choices
[List other decisions as they're created: 002-*.md, 003-*.md, etc.]

### Knowledge and Patterns
- @context/knowledge/patterns/*.md - Coding patterns to follow
- @context/knowledge/anti-patterns/*.md - Patterns to avoid

### Feature-Specific Context
- @context/intent/feature-*.md - Load relevant feature intents when working on specific features
- @context/intent/bug-*.md - Load bug intents when fixing bugs

**How to use**: When an AI agent starts working, it should load the relevant Context Mesh files above to understand the strategic context (what, why, how decided) before executing operational tasks.

## Project Structure

```
root/
├── AGENTS.md              # This file (router for AI agents)
├── context/               # Context Mesh: strategic context
│   ├── intent/
│   │   ├── project-intent.md
│   │   ├── feature-*.md
│   │   └── bug-*.md
│   ├── decisions/
│   │   └── 001-*.md, 002-*.md, ...
│   ├── knowledge/
│   │   ├── patterns/
│   │   └── anti-patterns/
│   ├── agents/            # Optional: specialized agent definitions
│   │   └── agent-*.md
│   └── evolution/
│       ├── changelog.md
│       └── learning-*.md
└── [your code]
```

## Development Workflow

### Step 1: Load Context
Before starting work, load relevant Context Mesh files:
- @context/intent/project-intent.md (always)
- @context/intent/feature-*.md (if working on specific feature)
- @context/decisions/*.md (relevant decisions)
- @context/knowledge/patterns/*.md (relevant patterns)

### Step 2: Follow Context Mesh Workflow
1. **Intent**: Understand what to build (from Context Mesh)
2. **Build**: Generate code following patterns and decisions
3. **Learn**: Update context after changes

### Step 3: Execute
- Follow code style and conventions
- Run tests before committing
- **Always update context** - Update Context Mesh files after implementation (see "Critical: Always Update Context After Changes" below)

## AI Agent Behavior

### Allowed
- Create/edit code following Context Mesh patterns
- Reference decisions from `@context/decisions/`
- Follow patterns from `@context/knowledge/patterns/`
- Update context when implementation differs from plan

### Forbidden
- Modifying `package.json` or config files without explicit instruction
- Ignoring decisions from `@context/decisions/`
- Using anti-patterns from `@context/knowledge/anti-patterns/`
- Changing project structure without updating context

### Critical: Always Update Context After Changes

**IMPORTANT**: After implementing, creating, or modifying code, AI agents MUST update Context Mesh:

1. **After creating new files/modules**:
   - Update relevant feature intent if scope changed
   - Create or update decision if new technical approach was used
   - Update changelog.md

2. **After modifying existing code**:
   - Update feature intent if functionality changed
   - Update decision outcomes if approach differed from plan
   - Update changelog.md

3. **After completing work**:
   - Mark feature/bug as completed in intent file
   - Add outcomes to decision files
   - Document learnings in evolution/learning-*.md
   - Update changelog.md

**How to update context:**
- After implementation, update relevant Context Mesh files:
  - Mark feature/bug as completed in intent file
  - Add outcomes to decision files
  - Update changelog.md
  - Document learnings if significant
- You can use AI to help identify what needs updating

**Never leave context stale** - Context Mesh only works if context reflects reality.

## Definition of Done (Project/Feature Level)

This is the **project-level DoD** that every feature must meet before being considered complete. This is different from:
- **Success Criteria**: Functional requirements in `feature-*.md` (acceptance criteria)

Before completing a feature:
- [ ] Code follows patterns from Context Mesh
- [ ] Decisions from Context Mesh are respected
- [ ] Tests passing
- [ ] Linter passing
- [ ] **Context updated** - Context Mesh files updated to reflect implementation
- [ ] Feature/bug marked as completed in intent file
- [ ] Decision outcomes added (if applicable)
- [ ] Changelog updated
- [ ] Code linked to relevant intent/decisions
- [ ] Success Criteria met (from `feature-*.md` - acceptance criteria)
---

Analyze my codebase and create all these files with appropriate content based on what you find.
```

---

## Execute: Continue Building

After Context Mesh is added, use this simple prompt to continue building:

```
Now load the @context files and continue building.
```

The AI will:
1. Load all context files (project-intent.md, decisions, feature intents, patterns)
2. Continue building following the documented context
3. Follow patterns from context/knowledge/

---

## What This Prompt Creates

- **Complete Context Mesh structure** - Documents existing codebase
- **project-intent.md** - Extracted from codebase
- **feature-*.md** - One per identified feature
- **decisions/*.md** - Technical decisions inferred from code
- **patterns/*.md** - Patterns found in codebase
- **changelog.md** - Current state documented
- **AGENTS.md** - Router file with Context Mesh integration

---

## Optional: Next Steps

If you want to add more later:
- **Add a feature**: Use `add-feature.md` prompt
- **Update a feature**: Use `update-feature.md` prompt
- **Fix a bug**: Use `fix-bug.md` prompt
- **Create agent**: Use `create-agent.md` prompt for reusable patterns

**Note**: The AI will automatically update context after implementation if you have AGENTS.md. If not, you can manually use `learn-update.md` prompt.
