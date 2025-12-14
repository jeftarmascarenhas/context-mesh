# Prompt: Initialize Context Mesh for New Project

Use this prompt when starting a brand new project from scratch.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer the questions** as the AI asks
4. **Review** the generated files
5. **Execute** - Use the execution prompt below to build

---

## Prompt

```
I'm starting a new project and want to use Context Mesh to maintain context throughout development.

Context Mesh is a simple framework with 3 steps:
1. Intent - Define what to build and why
2. Build - AI generates code, human supervises
3. Learn - Update context with learnings

Please help me set up Context Mesh by asking me about my project, then create the complete structure.

Ask me:
1. What is the project name?
2. What type of project? (web app, API, mobile app, CLI, library, etc.)
3. What problem does it solve? (main purpose)
4. Why is this project important? (business value, learning, etc.)
5. What are the main features you plan to build?
6. What tech stack? (if known)
7. How will you know the project is successful? (success criteria)

After I answer, create this folder structure:

context/
├── intent/
│   ├── project-intent.md
│   └── feature-[name].md (one per main feature)
├── decisions/
│   └── 001-tech-stack.md (if tech stack provided)
├── knowledge/
│   ├── patterns/
│   └── anti-patterns/
├── agents/        # Optional: for reusable execution patterns
│   └── agent-*.md
└── evolution/
    └── changelog.md

Also create AGENTS.md file at project root following the template below.

Use these templates:

---
PROJECT-INTENT.MD TEMPLATE:
---
# Project Intent: [PROJECT_NAME]

## What
[Project description - what it does]

## Why
[Why this project exists - business value, problem it solves]

## Success Criteria
- [Criterion 1]
- [Criterion 2]
- [Criterion 3]

## Scope
- [Main feature 1]
- [Main feature 2]
- [Main feature 3]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

---
FEATURE-[NAME].MD TEMPLATE:
---
# Feature: [FEATURE_NAME]

## What
[What this feature does]

## Why
[Why we need this feature]

## Success Criteria
- [Criterion 1]
- [Criterion 2]

## Related
- Intent: project-intent.md

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

---
DECISIONS/001-TECH-STACK.MD TEMPLATE (if tech stack provided):
---
# Decision: Tech Stack

## Context
Starting a new [PROJECT_TYPE] project and need to choose technologies.

## Decision
- Frontend: [if applicable]
- Backend: [if applicable]
- Database: [if applicable]
- Other: [other technologies]

## Rationale
[Why these technologies were chosen]

## Alternatives
- [Alternative 1]
- [Alternative 2]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
---

---
CHANGELOG.MD TEMPLATE:
---
# Changelog

## [Unreleased]

### Added
- Project initialized with Context Mesh
- Created project intent
- Created feature intents: [list features]

### Changed

### Fixed

---
*Last Updated: [TODAY'S DATE]*
---

---
AGENTS.MD TEMPLATE (create this file at project root):
---
# AGENTS.md

## Setup Commands

[Based on tech stack - add install, dev, test, build commands]
Example:
- Install deps: `npm install` or `pnpm install`
- Start dev server: `npm run dev`
- Run tests: `npm test`
- Build: `npm run build`

## Code Style

[Based on tech stack - add conventions]
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

## Definition of Done (Technical/Feature Level - Step 2: Build Only)

**Important**: DoD applies only to **Step 2 (Build)** when implementing features technically. Steps 1 (Intent) and 3 (Learn) don't have DoD - they have flexible "Outputs" instead.

This is the **technical/feature-level DoD** that every feature implementation must meet before being considered complete. This is different from:
- **Success Criteria**: Functional requirements in `feature-*.md` (acceptance criteria)

**When to apply**: Only during Step 2 (Build) when implementing code, not during Step 1 (Intent) or Step 3 (Learn).

Before completing a feature implementation (Step 2 - Build):
- [ ] Technical decision (ADR) verified or created before implementation - **Required**
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

Create all files with proper content based on my answers.
```

---

## Execute: Build the Project

After the Context Mesh structure is created, use this simple prompt to build:

```
Now load the @context files and build the project.
```

The AI will:
1. Load all context files (project-intent.md, decisions, feature intents)
2. Generate code following the tech stack decision
3. Implement features according to their intents
4. Follow patterns from context/knowledge/

**That's it!** Your project will be built based on your context.

---

## What This Prompt Creates

- **Complete Context Mesh structure** - All folders and initial files
- **project-intent.md** - Main intent document
- **feature-*.md** - Feature intents (one per main feature)
- **001-tech-stack.md** - Tech stack decision (if provided)
- **changelog.md** - Initial changelog
- **AGENTS.md** - Router file for AI agents with Context Mesh integration

---

## Optional: Next Steps

If you want to add more later:
- **Add a feature**: Use `add-feature.md` prompt
- **Update a feature**: Use `update-feature.md` prompt
- **Fix a bug**: Use `fix-bug.md` prompt
- **Create agent**: Use `create-agent.md` prompt for reusable patterns

**Note**: The AI will automatically update context after implementation if you have AGENTS.md. If not, you can manually use `learn-update.md` prompt.
