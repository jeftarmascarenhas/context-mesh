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

**FIRST: Load framework context:**
- Load @context/.context-mesh-framework.md (if exists) to understand Context Mesh framework rules and file type separation
- Understand that features, decisions, and patterns MUST be separated
- Features = What and Why (business/user value)
- Decisions = Technical choices and approaches (HOW)
- Patterns = Code patterns and examples (HOW TO IMPLEMENT)

Analyze my codebase and extract:
1. Project structure (directories, files, config)
2. Technologies used (package.json, requirements.txt, etc.)
3. Key features/modules already implemented
4. Patterns found in the code
5. Technical decisions that were made

**CRITICAL: Separate concerns correctly:**
- **Feature files** (`feature-*.md`) should contain ONLY: What the feature does, Why it exists (business/user value), Acceptance criteria (if applicable)
- **Decision files** (`decisions/*.md`) should contain: Technical choices (which library, which approach, which architecture), Rationale, Alternatives
- **Pattern files** (`knowledge/patterns/*.md`) should contain: Code examples, Implementation patterns, How to use the pattern

**When analyzing code:**
- If you find technical choices (libraries, frameworks, approaches) → Create a DECISION file
- If you find code patterns or implementation examples → Create a PATTERN file
- Feature files should reference decisions and patterns, NOT contain technical details

Then create this structure to document the existing codebase:

context/
├── .context-mesh-framework.md (ALWAYS create - framework rules and patterns)
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

.CONTEXT-MESH-FRAMEWORK.MD (ALWAYS create this file):
---
**IMPORTANT**: This file should contain the complete Context Mesh framework reference. 

If you have access to the Context Mesh framework repository, copy the content from `context/.context-mesh-framework.md`.

If you don't have access, create a file that includes:
- Framework overview (3 steps: Intent → Build → Learn)
- File type separation rules (Feature, Decision, Knowledge, Agent files)
- Plan, Approve, Execute pattern (MANDATORY)
- When to create vs not create files
- Context structure
- Definition of Done
- Bidirectional links rules
- Status section requirements

This file is critical for AI agents to understand and follow Context Mesh rules correctly.
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
[What this feature does - functional description, NOT technical implementation]

**IMPORTANT**: Describe WHAT the feature does from a user/business perspective, NOT how it's implemented technically.

## Why
[Why this feature exists - business value, user need, problem it solves]

**IMPORTANT**: Focus on business/user value, NOT technical reasons.

## Acceptance Criteria
[Functional requirements - what must work, NOT how it's implemented]
- [ ] [Functional criterion 1]
- [ ] [Functional criterion 2]

**IMPORTANT**: Do NOT include:
- ❌ Technical implementation details (→ put in Decision file)
- ❌ Code examples or structure (→ put in Pattern file)
- ❌ Library names or technical choices (→ put in Decision file)
- ❌ File paths or code structure (→ put in Pattern file if it's a pattern)

## Related
- [Project Intent](project-intent.md)
- [Decision: [Decision Name]](../decisions/[number]-[decision-name].md) (MUST link to decision if technical approach exists)
- [Pattern: [Pattern Name]](../knowledge/patterns/[pattern-name].md) (if implementation pattern exists)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Active (already implemented)
---

DECISIONS/001-TECH-STACK.MD (and other decision files):
---
# Decision: [DECISION_NAME]

## Context
[Situation, requirements, constraints that led to this technical choice]

**For existing projects**: Document what you can infer from code, comments, or documentation.

## Decision
[Technical choice/approach that was selected]

**Examples:**
- "Use Next.js App Router for routing"
- "Use next-intl for internationalization"
- "Use JWT tokens for authentication"
- "Use Prisma ORM for database access"

**IMPORTANT**: This is the technical CHOICE, not the feature requirement.

## Rationale
[Why this approach was chosen - technical reasons]

**For existing projects**: Infer from code patterns, dependencies, or documentation. If unclear, note: "Rationale not documented in existing codebase, inferred from implementation."

## Alternatives Considered
[Other options that could have been used and why they weren't chosen]

**For existing projects**: If alternatives can be inferred from code/comments/documentation, list them. Otherwise, note: "Alternatives not documented in existing codebase."

## Outcomes
[To be updated after future changes in Step 3: Learn]

**For existing projects**: Leave empty or note: "Outcomes to be documented as project evolves."

## Related
- [Project Intent](../intent/project-intent.md)
- [Feature: [Feature Name]](../intent/feature-[name].md) (if this decision applies to a specific feature)
- [Decision: [Other Decision]]([number]-[other].md) (if this decision relates to another)

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
- **Note**: Documented from existing implementation
---

**IMPORTANT**: Create separate decision files for:
- Tech stack choices (001-tech-stack.md)
- Feature-specific technical approaches (002-[feature]-approach.md, etc.)
- Architecture decisions
- Library/framework choices for specific features

PATTERNS/[PATTERN-NAME].MD:
---
# Pattern: [PATTERN_NAME]

## Description
[What this pattern is - clear description of the pattern]

## When to Use
[When to apply this pattern - specific scenarios or contexts]

## Pattern
[The pattern itself - structure, approach, or convention]

## Example
[Code example from the codebase showing the pattern]

**IMPORTANT**: Include actual code examples showing how the pattern is used.

## Files Using This Pattern
- [file1.ts] - [brief note on how it's used]
- [file2.ts] - [brief note on how it's used]

## Related
- [Decision: [Decision Name]](../decisions/[number]-[decision-name].md) (if this pattern relates to a decision)
- [Feature: [Feature Name]](../intent/feature-[name].md) (if this pattern is used by a feature)

## Status
- **Created**: [TODAY'S DATE]
- **Status**: Active
---

**IMPORTANT**: Create pattern files when you find:
- Reusable code structures
- Implementation patterns (how to implement something)
- Code conventions
- Architecture patterns
- API design patterns

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

**CRITICAL SEPARATION RULES:**
1. **Feature files** should be HIGH-LEVEL: What and Why only, NO technical details
2. **Decision files** should contain: Technical choices, which library/approach, rationale
3. **Pattern files** should contain: Code examples, implementation patterns, how to use

**Example of correct separation:**

❌ **WRONG** (everything in feature):
```markdown
# Feature: SEO
## What
SEO optimization using Next.js Metadata API, Open Graph tags, structured data...
[Technical details mixed with feature description]
```

✅ **CORRECT** (separated):
```markdown
# Feature: SEO Optimization
## What
Comprehensive SEO optimization to improve search visibility and rankings.
## Why
Improve organic traffic and search engine rankings.
## Related
- [Decision: Next.js Metadata API](../decisions/002-seo-approach.md)
- [Pattern: SEO Metadata](../knowledge/patterns/seo-metadata.md)
```

```markdown
# Decision: SEO Approach
## Decision
Use Next.js Metadata API for SEO
## Rationale
[Technical reasons]
```

```markdown
# Pattern: SEO Metadata
## Example
[Code example showing how to implement]
```

**Bidirectional Links**: Create proper links between features, decisions, and patterns:
- Feature files must link to their decision files: `- [Decision: Name](../decisions/[number]-[name].md)`
- Decision files must link back to features: `- [Feature: Name](../intent/feature-[name].md)`
- Feature files can link to patterns: `- [Pattern: Name](../knowledge/patterns/[pattern-name].md)`
- Pattern files should link to related decisions: `- [Decision: Name](../decisions/[number]-[name].md)`
- Use markdown link format: `- [Type: Name](path/to/file.md)`
- Links should be bidirectional where applicable
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
