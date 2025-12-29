# Prompt: Initialize Context Mesh for New Project

Use this prompt when starting a brand new project from scratch.

**What gets created?** A `context/` folder structure that captures:
- **Intent** - What you're building and why
- **Decisions** - Technical choices (ADRs)
- **Knowledge** - Patterns and anti-patterns
- **Evolution** - Changelog and learnings

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
5. Main features to build?
   - For each feature, also ask:
     - What does this feature do and why do we need it?
     - Acceptance criteria for this feature?
     - Technical approach for this feature? (What technical solution will be used?)
     - Why this approach? (Rationale)
     - What alternatives did you consider?
6. Tech stack? (if known)
   - If tech stack provided, also ask:
     - Why this tech stack? (Rationale)
     - What alternatives did you consider?
7. Project acceptance criteria? (overall project criteria)

Then create this structure:

context/
├── intent/
│   ├── project-intent.md
│   └── feature-[name].md (one per main feature, with complete information)
├── decisions/
│   ├── 001-tech-stack.md (if tech stack provided)
│   └── [002+]-[feature-name].md (one per feature, starting from 002 if tech-stack exists, or 001 if not)
├── knowledge/
│   ├── patterns/
│   └── anti-patterns/
├── agents/
│   └── (empty for now)
└── evolution/
    └── changelog.md

Also create AGENTS.md at project root.

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
- Created feature intents: [list]
- Created feature decisions: [list]

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
- **Creates `feature-*.md`** - One per feature you defined (complete with What, Why, Acceptance Criteria)
- **Creates `001-tech-stack.md`** - If tech stack was provided
- **Creates `[next-number]-[feature-name].md`** - One decision per feature (technical approach with rationale and alternatives)
- **Creates `changelog.md`** - Initial changelog
- **Creates `AGENTS.md`** - AI agent router at project root

**Note**: Each feature gets both an intent file (What/Why) and a decision file (How). This ensures features are complete and ready for implementation.

---

## Next Steps

- **Add feature**: Use `add-feature.md`
- **Fix bug**: Use `fix-bug.md`
- **Update feature**: Use `update-feature.md`

**Note**: AI updates context automatically if AGENTS.md exists.
