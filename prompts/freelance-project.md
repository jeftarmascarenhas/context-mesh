# Prompt: Initialize Context Mesh for Freelance/Client Project

Use this prompt when starting a freelance or client project.

**Why use this for client work?** Captures client requirements as living documentation:
- Client name, deliverables, deadlines
- Acceptance criteria (how client knows it's done)
- Technical constraints
- Clear scope to avoid scope creep

## How to Use

1. **Copy** the prompt below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** questions or paste client brief
4. **Review** generated files
5. **Build** - Use the execution prompt to start coding

---

## Prompt

```
I'm starting a freelance/client project with Context Mesh.

Ask me:
1. Client/project name?
2. Project type? (website, web app, mobile, API, etc.)
3. Do you have a client brief? (I'll paste it)
4. Main deliverables/features?
5. Timeline/deadline?
6. Tech requirements or constraints?
7. Acceptance criteria? (How will client know it's done?)

Then create this structure:

context/
├── intent/
│   ├── project-intent.md (from client requirements)
│   └── feature-[name].md (one per deliverable)
├── decisions/
│   └── (populated as decisions are made)
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

PROJECT-INTENT.MD (client project):
---
# Project Intent: [CLIENT/PROJECT_NAME]

## Client
[Client name/company]

## What
[Project description from brief]

## Why
[Client's business needs]

## Deliverables
- [Deliverable 1]
- [Deliverable 2]

## Acceptance Criteria
- [Client criterion 1]
- [Client criterion 2]

## Timeline
- **Deadline**: [Date if provided]
- **Milestones**: [If any]

## Constraints
- [Technical constraints]
- [Budget constraints]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

FEATURE-[NAME].MD (deliverable):
---
# Feature: [DELIVERABLE_NAME]

## What
[What needs to be built]

## Why
[Business value for client]

## Acceptance Criteria
- [Client criterion 1]
- [Client criterion 2]

## Related
- Intent: project-intent.md
- Decision: [number]-[decision-name].md (if applicable)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

CHANGELOG.MD:
---
# Changelog

## [Unreleased]

### Added
- Project initialized with Context Mesh
- Documented client requirements
- Created deliverable intents: [list]

### Delivered

### Changed

---
*Project Start: [TODAY'S DATE]*
*Deadline: [DEADLINE IF PROVIDED]*
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
- @context/intent/feature-*.md (for specific deliverable)
- @context/decisions/*.md (relevant decisions)
- @context/knowledge/patterns/*.md (patterns to follow)

## Project Structure
```
root/
├── AGENTS.md
├── context/
│   ├── intent/
│   ├── decisions/
│   ├── knowledge/
│   ├── agents/
│   └── evolution/
└── [code]
```

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
- [ ] Acceptance Criteria met (client requirements)
---

Create all files based on client requirements.
```

---

## Execute: Start Building

After Context Mesh is created:

```
Load @context files and build the project.
```

---

## What This Prompt Does

- **Creates `context/` folder** with complete structure
- **Creates `project-intent.md`** - Documents client requirements
- **Creates `feature-*.md`** - One per deliverable
- **Creates `changelog.md`** - With project timeline
- **Creates `AGENTS.md`** - AI agent router at project root

---

## Next Steps

- **Add feature**: Use `add-feature.md`
- **Fix bug**: Use `fix-bug.md`
- **Update feature**: Use `update-feature.md`

**Note**: AI updates context automatically if AGENTS.md exists.
