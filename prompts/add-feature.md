# Prompt: Add New Feature

Use this prompt to add a new feature to a project that already uses Context Mesh.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer questions** about the new feature
4. **Review** the generated files

---

## Prompt

```
I'm adding a new feature to my project that uses Context Mesh.

Context Mesh workflow:
1. Intent - Define what to build and why (create feature intent + decision before coding)
2. Build - AI generates code following decisions
3. Learn - Update context after implementation

Please help me create the context files for this new feature.

Ask me:
1. What is the feature name?
2. What does this feature do? (What problem does it solve?)
3. Why are we building this feature? (Business value, user need)
4. What are the success criteria? (How will we know it's complete?)
5. Does this relate to existing features? (Which ones?)
6. What technical approach will you use? (This becomes the decision/ADR)
7. Does this change the project scope?

After I answer, create these files:

1. context/intent/feature-[name].md - The feature intent
2. context/decisions/[number]-[decision].md - Technical decision (ADR) for the approach
3. Update changelog.md - Add the new feature to changelog
4. Update AGENTS.md - Add the new feature intent to "Context Files to Load" section under "Feature-Specific Context" if it doesn't exist

IMPORTANT: The technical decision (ADR) must be created BEFORE implementation.

Use these templates:

---
FEATURE-[NAME].MD TEMPLATE:
---
# Feature: [FEATURE_NAME]

## What
[What this feature does]

## Why
[Why we need this feature - business value]

## Success Criteria
- [Criterion 1]
- [Criterion 2]

## Technical Approach
See: decisions/[number]-[decision-name].md

## Related
- Intent: project-intent.md
- Decision: [number]-[decision-name].md
- Related Features: [if any]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

---
DECISIONS/[NUMBER]-[NAME].MD TEMPLATE:
---
# Decision: [TECHNICAL APPROACH TITLE]

## Context
Adding [FEATURE_NAME] feature and need to decide on technical approach.

## Decision
[What approach was chosen]

## Rationale
[Why this approach was chosen]

## Alternatives
- [Alternative 1] - [why not chosen]
- [Alternative 2] - [why not chosen]

## Implementation Notes
- [Key implementation detail 1]
- [Key implementation detail 2]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
---

---
ADD TO CHANGELOG.MD:
---
## [Unreleased]

### Added
- Feature: [FEATURE_NAME] - [brief description]
---

Create all files based on my answers. Remember: decision (ADR) must exist before implementation starts.
```

---

## What This Prompt Does

- **Creates feature intent** - Documents what and why
- **Creates technical decision (ADR)** - Documents how (required before implementation)
- **Updates changelog** - Tracks the new feature
- **Links everything** - Connects feature to decisions and project

---

## Important: ADR Before Implementation

Context Mesh requires a technical decision (ADR) to exist **before** you start implementing a feature. This ensures:
- Technical choices are documented
- Rationale is captured
- Alternatives are considered

---

## Execute: Build the Feature

After the context files are created, use this simple prompt to build:

```
Now load the @context files and implement the feature.
```

The AI will:
1. Load feature intent and decision files
2. Generate code following the technical decision
3. Implement according to the feature intent

---

## After Using This Prompt

1. **Review feature intent** - Check if it accurately describes the feature
2. **Review decision** - Ensure technical approach is documented
3. **Execute** - Use the execution prompt above to build

**Note**: The AI will automatically update context after implementation if you have AGENTS.md. If not, you can manually use `learn-update.md` prompt.

---

## Optional: Next Steps

- **Feature changes?** Use `update-feature.md`
- **Found a bug?** Use `fix-bug.md`
