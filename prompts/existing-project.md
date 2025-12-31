# Prompt: Add Context Mesh to Existing Project

Use this prompt to add Context Mesh to an existing codebase.

**What does this do?** AI analyzes your code and creates living documentation:
- Extracts what the project does and why
- Documents existing features
- Identifies patterns already in your code
- Creates a foundation for future changes

## How to Use

1. **Copy the prompt** below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Let AI analyze** your codebase
4. **Review** generated files and adjust if needed
5. **Done** - Context Mesh is now your living documentation

---

## Prompt

```
I have an existing project and want to add Context Mesh to document what already exists.

Analyze my codebase and extract:
1. Project structure (directories, files, config)
2. Technologies used (package.json, requirements.txt, etc.)
3. Key features/modules already implemented
4. Patterns found in the code
5. Technical decisions that were made

Then create this structure to document the existing codebase:

context/
├── intent/
│   ├── project-intent.md (what the project does - from analysis)
│   └── feature-[name].md (one per identified feature/module)
├── decisions/
│   ├── 001-tech-stack.md (from package.json, etc.)
│   └── 002-[other].md (other decisions inferred from code)
├── knowledge/
│   ├── patterns/
│   │   └── [identified-pattern].md
│   └── anti-patterns/
├── agents/
│   └── (empty for now)
└── evolution/
    └── changelog.md (document current state)

Also create AGENTS.md at project root.

---
TEMPLATES:
---

PROJECT-INTENT.MD:
---
# Project Intent: [PROJECT_NAME]

## What
[What project does - extracted from code analysis]

## Why
[Why it exists - inferred from code/docs/README]

## Current State
[Current state of the project - what's implemented]

## Current Features
- [Feature 1 - identified from code]
- [Feature 2 - identified from code]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active
- **Note**: Generated from existing codebase analysis
---

FEATURE-[NAME].MD:
---
# Feature: [FEATURE_NAME]

## What
[What this feature does - from code analysis]

## Why
[Inferred purpose]

## Current Implementation
- [How it's currently implemented]
- [Key files involved]

## Related
- [Project Intent](project-intent.md)
- [Decision: [Decision Name]](../decisions/[number]-[decision-name].md) (if applicable)
- Files: [list key files for this feature]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active (already implemented)
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
- Key Dependencies: [key deps from package.json, etc.]

## Rationale
[Inferred from code patterns and choices - why these technologies were likely chosen]

## Alternatives Considered
[If alternatives can be inferred from code/comments/documentation, list them. Otherwise, note: "Alternatives not documented in existing codebase."]

## Outcomes
[To be updated after future changes in Step 3: Learn]

## Related
- [Project Intent](../intent/project-intent.md)
- [Feature: [Feature Name]](../intent/feature-[name].md) (if applicable)
- [Decision: [Other Decision]]([number]-[other].md) (if applicable)

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
[When to apply this pattern]

## Example
[Code example from the codebase]

## Files Using This Pattern
- [file1.ts]
- [file2.ts]

## Status
- **Created**: [TODAY'S DATE]
- **Status**: Active
---

CHANGELOG.MD:
---
# Changelog

## [Current State] - Context Mesh Added

### Existing Features (documented)
- [Feature 1] - [brief description]
- [Feature 2] - [brief description]

### Tech Stack (documented)
- [Technology 1]
- [Technology 2]

### Patterns Identified
- [Pattern 1]
- [Pattern 2]

---
*Context Mesh added: [TODAY'S DATE]*
*This changelog documents the state when Context Mesh was added.*
*Future changes will be tracked below.*
---

AGENTS.MD (at project root):
---
# AGENTS.md

## Setup Commands
[Extracted from package.json, README, Makefile, etc.]
- Install: `[detected command]`
- Dev: `[detected command]`
- Test: `[detected command]`
- Build: `[detected command]`

## Code Style
[Extracted from codebase analysis]
- [Detected convention 1]
- [Detected convention 2]
- Follow patterns from `@context/knowledge/patterns/`

## Context Files to Load

Before starting any work, load relevant context:
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
└── [existing code]

## AI Agent Rules

### Always
- Load context before implementing
- Follow decisions from @context/decisions/
- Use patterns from @context/knowledge/patterns/
- Update context after any changes

### Never
- Ignore documented decisions
- Use anti-patterns from @context/knowledge/anti-patterns/
- Leave context stale after changes

### After Any Changes (Critical)
AI must update Context Mesh after changes:
- Update relevant feature intent if functionality changed
- Add outcomes to decision files if approach differed
   - Update changelog.md
- Create learning-*.md if significant insights

## Definition of Done (Build Phase)

Before completing any implementation:
- [ ] ADR exists before implementation
- [ ] Code follows documented patterns
- [ ] Decisions respected
- [ ] Tests passing
- [ ] Context updated to reflect changes
- [ ] Changelog updated

---

**Note**: This is a basic AGENTS.md template. For a complete template with advanced features (File Creation Rules, Execution Agents, etc.), see `examples/AGENTS.md.example`.
---

Analyze my codebase and create all files with content based on what you find.
Important: This is documentation of what EXISTS, not what needs to be built.

**Bidirectional Links**: Create proper links between features and decisions:
- Feature files must link to their decision files using format: `- [Decision: Name](../decisions/[number]-[name].md)`
- Decision files must link back to their feature files using format: `- [Feature: Name](../intent/feature-[name].md)`
- Use markdown link format: `- [Type: Name](path/to/file.md)`
- Links should be bidirectional (feature ↔ decision)
```

---

## What This Prompt Does

Documents your **existing codebase** as living context:

- **Creates `project-intent.md`** - What the project does (extracted from code)
- **Creates `feature-*.md`** - Each existing feature documented
- **Creates `decisions/*.md`** - Technical decisions already made
- **Creates `patterns/*.md`** - Patterns found in your code
- **Creates `changelog.md`** - Current state documented
- **Creates `AGENTS.md`** - AI agent router for future work

---

## After Running This Prompt

Your project now has **living documentation**. From here:

| I want to... | Use this prompt |
|--------------|-----------------|
| Add a new feature | [add-feature.md](add-feature.md) |
| Update existing feature | [update-feature.md](update-feature.md) |
| Fix a bug | [fix-bug.md](fix-bug.md) |
| Update context after changes | AI does automatically, or use [learn-update.md](learn-update.md) |

---

## Tips

1. **Review generated files** - AI inference may need adjustments
2. **Add missing context** - Add any context AI couldn't infer
3. **Keep it updated** - Context Mesh only works if it reflects reality
4. **Don't over-document** - Focus on what matters for future development

---

## Why This Matters

Without Context Mesh:
```
"Why was this built this way?" → Hours reconstructing context
```

With Context Mesh:
```
"Why was this built this way?" → Check @context/decisions/
```

Your existing codebase now has preserved context for:
- Future you
- New team members
- AI assistants
