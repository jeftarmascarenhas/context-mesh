# Prompt: Add Context Mesh to Existing Project

Use this prompt when you have an existing project and want to add Context Mesh.

## How to Use

1. **Copy the prompt** below (inside the ` ``` ` block)
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Let AI analyze** your codebase
4. **Review** generated files
5. **Continue** - Use the execution prompt to keep building

---

## Prompt

```
I have an existing project and want to add Context Mesh to document and maintain context.

Analyze my codebase:
1. Project structure (directories, files, config)
2. Technologies used (package.json, requirements.txt, etc.)
3. Key features/modules
4. Patterns in the code
5. Technical decisions already made

Then create this structure:

context/
├── intent/
│   ├── project-intent.md (from analysis)
│   └── feature-[name].md (one per identified feature)
├── decisions/
│   ├── 001-tech-stack.md (from package.json, etc.)
│   └── 002-[other].md (inferred from code)
├── knowledge/
│   ├── patterns/
│   │   └── [identified-pattern].md
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
[What project does - from analysis]

## Why
[Why it exists - inferred from code/docs]

## Success Criteria
- [Inferred criterion 1]
- [Inferred criterion 2]

## Current Features
- [Feature 1 - from code]
- [Feature 2 - from code]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active
- **Note**: Generated from codebase analysis
---

FEATURE-[NAME].MD:
---
# Feature: [FEATURE_NAME]

## What
[What this feature does - from analysis]

## Why
[Inferred purpose]

## Current Implementation
- [How it's implemented]

## Related
- Intent: project-intent.md
- Files: [key files for this feature]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active
---

DECISIONS/001-TECH-STACK.MD:
---
# Decision: Tech Stack

## Context
Existing project with established technologies.

## Decision
- Frontend: [detected]
- Backend: [detected]
- Database: [detected]
- Dependencies: [key deps]

## Rationale
[Inferred from code patterns]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
- **Note**: Documented from existing implementation
---

PATTERNS/[PATTERN-NAME].MD:
---
# Pattern: [PATTERN_NAME]

## Description
[What this pattern is]

## When to Use
[When to apply]

## Example
[Code example from codebase]

## Status
- **Created**: [TODAY'S DATE]
- **Status**: Active
---

CHANGELOG.MD:
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
---

AGENTS.MD (at project root):
---
# AGENTS.md

## Setup Commands
[From package.json, README, etc.]
- Install: `[detected command]`
- Dev: `[detected command]`
- Test: `[detected command]`
- Build: `[detected command]`

## Code Style
[From codebase analysis]
- [Detected convention 1]
- [Detected convention 2]
- Follow patterns from `@context/knowledge/patterns/`

## Context Files to Load

Before starting work, load:
- @context/intent/project-intent.md (always)
- @context/intent/feature-*.md (for specific feature)
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
└── [existing code]
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
- [ ] Success Criteria met
---

Analyze my codebase and create all files with appropriate content.
```

---

## Execute: Continue Building

After Context Mesh is added:

```
Load @context files and continue building.
```

---

## What This Prompt Creates

- `context/` folder with complete structure
- `project-intent.md` - Extracted from codebase
- `feature-*.md` - One per identified feature
- `decisions/*.md` - Inferred from code
- `patterns/*.md` - Patterns found in code
- `changelog.md` - Current state
- `AGENTS.md` - AI agent router

---

## Next Steps

- **Add feature**: Use `add-feature.md`
- **Fix bug**: Use `fix-bug.md`
- **Update feature**: Use `update-feature.md`

**Note**: AI updates context automatically if AGENTS.md exists.
