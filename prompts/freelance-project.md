# Prompt: Initialize Context Mesh for Freelance/Client Project

Use this prompt when starting a freelance or client project to document requirements clearly.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer questions** or paste your client brief
4. **Review** the generated context files
5. **Execute** - Use the execution prompt below to start building

---

## Prompt

```
I'm starting a freelance/client project and want to use Context Mesh to:
1. Document client requirements clearly
2. Track technical decisions
3. Maintain context throughout delivery
4. Deliver maintainable code

Context Mesh is a simple framework with 3 steps:
1. Intent - Define what to build and why
2. Build - AI generates code, human supervises
3. Learn - Update context with learnings

Please help me set up Context Mesh for this client project.

Ask me:
1. What is the client/project name?
2. What type of project? (website, web app, mobile app, API, etc.)
3. Do you have a client brief? (If yes, I'll paste it)
4. What are the main deliverables/features?
5. What is the timeline/deadline?
6. Any technology requirements or constraints?
7. What are the acceptance criteria? (How will the client know it's done?)

After I provide the information, create this folder structure:

context/
├── intent/
│   ├── project-intent.md (from client requirements)
│   └── feature-[name].md (one per deliverable)
├── decisions/
│   └── (will be populated as technical decisions are made)
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
PROJECT-INTENT.MD TEMPLATE (for client projects):
---
# Project Intent: [CLIENT/PROJECT_NAME]

## Client
[Client name/company]

## What
[Project description based on client brief]

## Why
[Client's business needs and goals]

## Deliverables
- [Deliverable 1]
- [Deliverable 2]
- [Deliverable 3]

## Acceptance Criteria
- [Client acceptance criterion 1]
- [Client acceptance criterion 2]

## Timeline
- **Deadline**: [Date if provided]
- **Milestones**: [If any]

## Constraints
- [Technical constraints]
- [Budget constraints]
- [Other constraints]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

---
FEATURE-[NAME].MD TEMPLATE (for deliverables):
---
# Feature: [DELIVERABLE_NAME]

## What
[What needs to be built]

## Why
[Why the client needs it - business value]

## Acceptance Criteria
- [Client criterion 1]
- [Client criterion 2]

## Related
- Intent: project-intent.md

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

---
CHANGELOG.MD TEMPLATE:
---
# Changelog

## [Unreleased]

### Added
- Project initialized with Context Mesh
- Documented client requirements
- Created deliverable intents: [list deliverables]

### Delivered

### Changed

---
*Project Start: [TODAY'S DATE]*
*Deadline: [DEADLINE IF PROVIDED]*
---

---
AGENTS.MD TEMPLATE (create this file at project root):
---
# AGENTS.md

## Setup Commands

[Based on tech stack - add install, dev, test, build commands]
Example:
- Install deps: `npm install`
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
- [ ] Acceptance Criteria met (from `feature-*.md` - client requirements)
---

Create all files with content based on the client requirements I provide.
```

---

## Execute: Start Building

After Context Mesh is set up, use this simple prompt to start building:

```
Now load the @context files and build the project.
```

The AI will:
1. Load all context files (project-intent.md, feature intents with acceptance criteria)
2. Generate code following client requirements
3. Follow patterns from context/knowledge/

---

## What This Prompt Creates

- **Complete Context Mesh structure** - With client requirements
- **project-intent.md** - Client project intent with acceptance criteria
- **feature-*.md** - One per deliverable with acceptance criteria
- **changelog.md** - With project timeline
- **AGENTS.md** - Router file with Context Mesh integration

---

## Optional: Next Steps

If you want to add more later:
- **Add a feature**: Use `add-feature.md` prompt
- **Update a feature**: Use `update-feature.md` prompt
- **Fix a bug**: Use `fix-bug.md` prompt
- **Create agent**: Use `create-agent.md` prompt for reusable patterns

**Note**: The AI will automatically update context after implementation if you have AGENTS.md. If not, you can manually use `learn-update.md` prompt.
