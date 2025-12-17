# Prompt: Initialize Context Mesh for New Project

Use this prompt when starting a brand new project from scratch.

## How to Use

1. **Copy the prompt** below (inside the ` ``` ` block)
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
6. Tech stack? (if known)
7. Success criteria?

Then create this structure:

context/
├── intent/
│   ├── project-intent.md
│   └── feature-[name].md (one per main feature)
├── decisions/
│   └── 001-tech-stack.md (if tech stack provided)
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

## Success Criteria
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

## Success Criteria
- [Criterion 1]
- [Criterion 2]

## Related
- Intent: project-intent.md
- Decision: [number]-[decision-name].md (if applicable)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
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

## Rationale
[Why these technologies]

## Alternatives
- [Alternative 1]
- [Alternative 2]

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
- [ ] Success Criteria met
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

## What This Prompt Creates

- `context/` folder with complete structure
- `project-intent.md` - Main intent
- `feature-*.md` - One per feature
- `001-tech-stack.md` - If tech stack provided
- `changelog.md` - Initial changelog
- `AGENTS.md` - AI agent router

---

## Next Steps

- **Add feature**: Use `add-feature.md`
- **Fix bug**: Use `fix-bug.md`
- **Update feature**: Use `update-feature.md`

**Note**: AI updates context automatically if AGENTS.md exists.
