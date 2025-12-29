# Prompt: Initialize Context Mesh for New Project

Use this prompt when starting a brand new project from scratch.

**What gets created?** A `context/` folder structure that captures:
- **Intent** - What you're building and why (project-intent.md, optionally feature intents)
- **Decisions** - Technical choices (ADRs) - tech stack (if provided), optionally feature decisions
- **Knowledge** - Patterns and anti-patterns (structure ready)
- **Evolution** - Changelog and learnings (structure ready)

**Flexibility**: You can create features now or add them later using `add-feature.md`

## How to Use

1. **Copy** the prompt below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** the questions
4. **Review** generated files
5. **Build** - Use the execution prompt to start coding

---

## Prompt

```
I'm starting a new project with Context Mesh.

Ask me:
1. Project name?
2. Project type? (web app, API, mobile, CLI, library, etc.)
3. What problem does it solve?
4. Why is this important? (business value)
5. Project acceptance criteria? (overall project criteria)
6. Tech stack? (if known)
   - If tech stack provided, also ask:
     - Why this tech stack? (Rationale)
     - What alternatives did you consider?
7. Do you want to add features now? (y/n)
   - If YES: For each feature, ask:
     - Feature name?
     - What does this feature do and why do we need it?
     - Acceptance criteria for this feature?
     - Technical approach for this feature? (What technical solution will be used?)
     - Why this approach? (Rationale)
     - What alternatives did you consider?
   - If NO: Skip feature creation (user can use add-feature.md later)

Then create this structure:

context/
├── intent/
│   ├── project-intent.md
│   └── feature-[name].md (only if user answered YES to question 7, one per feature with complete information)
├── decisions/
│   ├── 001-tech-stack.md (if tech stack provided)
│   └── [002+]-[feature-name].md (only if features were created, one per feature, starting from 002 if tech-stack exists, or 001 if not)
├── knowledge/
│   ├── patterns/
│   └── anti-patterns/
├── agents/
│   └── (empty for now)
└── evolution/
    └── changelog.md

Also create AGENTS.md at project root.

**Note**: If user answered NO to question 7, inform them: "Project structure created. Use add-feature.md to add features when ready."

---
TEMPLATES:
---

PROJECT-INTENT.MD:
---
# Project Intent: [PROJECT_NAME]

## What
[Project description]

## Why
[Business value, problem it solves]

## Acceptance Criteria
- [Criterion 1]
- [Criterion 2]

## Scope
- [Feature 1]
- [Feature 2]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

FEATURE-[NAME].MD:
---
# Feature: [FEATURE_NAME]

## What
[What this feature does]

## Why
[Why we need it]

## Acceptance Criteria
- [Criterion 1]
- [Criterion 2]

## Related
- Intent: project-intent.md
- Decision: [number]-[feature-name].md (technical approach for this feature)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

DECISIONS/[NUMBER]-[FEATURE-NAME].MD (one per feature, starting from 002 if tech-stack exists, or 001 if not):
---
# Decision: [FEATURE_NAME] Technical Approach

## Context
Implementing [FEATURE_NAME] feature for [PROJECT_NAME]. Need to choose technical approach.

## Decision
[Technical solution that will be used for this feature]

## Rationale
[Why this approach - reasons for choosing this solution]

## Alternatives Considered
- [Alternative 1] - [Why not chosen]
- [Alternative 2] - [Why not chosen]

## Outcomes
[To be updated after implementation in Step 3: Learn]

## Related
- Intent: [feature-[name].md](../intent/feature-[name].md)
- Decision: [001-tech-stack.md](001-tech-stack.md) (if applicable)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
---

DECISIONS/001-TECH-STACK.MD (if tech stack provided):
---
# Decision: Tech Stack

## Context
Starting [PROJECT_TYPE] project, choosing technologies.

## Decision
- Frontend: [if applicable]
- Backend: [if applicable]
- Database: [if applicable]
- Key Dependencies: [if applicable]

## Rationale
[Why these technologies - reasons for choosing this stack]

## Alternatives Considered
- [Alternative 1] - [Why not chosen]
- [Alternative 2] - [Why not chosen]

## Outcomes
[To be updated after implementation in Step 3: Learn]

## Related
- Intent: [project-intent.md](../intent/project-intent.md)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
---

CHANGELOG.MD:
---
# Changelog

## [Unreleased]

### Added
- Project initialized with Context Mesh
- Created project intent
- Created feature intents: [list if features were created, otherwise omit]
- Created feature decisions: [list if features were created, otherwise omit]

### Changed

### Fixed

---
*Last Updated: [TODAY'S DATE]*
---

AGENTS.MD (at project root):
---
# AGENTS.md

## Setup Commands
- Install: `[package manager] install`
- Dev: `[package manager] run dev`
- Test: `[package manager] test`
- Build: `[package manager] run build`

## Code Style
- [Based on tech stack]
- Follow patterns from `@context/knowledge/patterns/`

## Context Files to Load

Before starting work, load:
- @context/intent/project-intent.md (always)
- @context/intent/feature-*.md (for specific feature)
- @context/decisions/*.md (relevant decisions)
- @context/knowledge/patterns/*.md (patterns to follow)

## Project Structure
root/
├── AGENTS.md
├── context/
│   ├── intent/
│   ├── decisions/
│   ├── knowledge/
│   ├── agents/           
│   └── evolution/
└── [code]

## AI Agent Rules

### Always
- Load context before implementing
- Follow decisions from @context/decisions/
- Use patterns from @context/knowledge/patterns/
- Update context after implementation

### Never
- Ignore documented decisions
- Use anti-patterns from @context/knowledge/anti-patterns/
- Leave context stale

### After Implementation (Critical)
AI must update Context Mesh after changes:
  - Mark feature/bug as completed in intent file
  - Add outcomes to decision files
  - Update changelog.md
- Create learning-*.md if significant insights

## Definition of Done (Build Phase)

Before completing implementation:
- [ ] ADR exists before implementation
- [ ] Code follows Context Mesh patterns
- [ ] Decisions respected
- [ ] Tests passing
- [ ] Context updated
- [ ] Changelog updated
- [ ] Acceptance Criteria met
---

Create all files based on my answers.

**Important**: 
- Always create project-intent.md, structure folders, and AGENTS.md
- Only create feature files and feature decisions if user answered YES to question 7
- If user answered NO to question 7, inform them they can use add-feature.md to add features later
```

---

## Execute: Build the Project

After Context Mesh is created:

```
Load @context files and build the project.
```

---

## What This Prompt Does

- **Creates `context/` folder** with complete structure
- **Creates `project-intent.md`** - Main project intent
- **Creates `001-tech-stack.md`** - If tech stack was provided (with rationale and alternatives)
- **Creates `changelog.md`** - Initial changelog
- **Creates `AGENTS.md`** - AI agent router at project root
- **Optionally creates features** - If you answer YES to "add features now":
  - **Creates `feature-*.md`** - One per feature (complete with What, Why, Acceptance Criteria)
  - **Creates `[next-number]-[feature-name].md`** - One decision per feature (technical approach with rationale and alternatives)

**Flexibility**: 
- **Start simple**: Answer NO to features question, then use `add-feature.md` when ready
- **Start complete**: Answer YES to features question, get everything set up at once

**Note**: If features are created, each feature gets both an intent file (What/Why) and a decision file (How). This ensures features are complete and ready for implementation.

---

## Next Steps

- **Add feature**: Use `add-feature.md` (if you didn't create features during initialization)
- **Fix bug**: Use `fix-bug.md`
- **Update feature**: Use `update-feature.md`
- **Start building**: Load @context files and begin implementation

**Note**: AI updates context automatically if AGENTS.md exists.

**Why this flexibility?**
- Some projects benefit from planning all features upfront
- Others benefit from starting simple and adding features as needed
- Context Mesh supports both approaches - choose what works for your project
