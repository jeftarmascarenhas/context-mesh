# Prompt: Update Existing Feature

Use this prompt to update or modify an existing feature in your Context Mesh project.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer questions** about the changes
4. **Review** the updated files

---

## Prompt

```
I need to update an existing feature in my project that uses Context Mesh.

Context Mesh workflow:
1. Intent - Update the feature intent with new requirements
2. Build - Implement changes following updated context
3. Learn - Update context after implementation

Please help me update the context files for this feature change.

Ask me:
1. Which feature are you updating? (feature name or file name)
2. What changes are you making to this feature?
3. Why are these changes needed? (Business reason, user feedback, etc.)
4. Do the success criteria change?
5. Does this require a new technical decision? (new approach, new technology)
6. Does this affect other features?

After I answer, do the following:

1. Update context/intent/feature-[name].md with the changes
2. If new technical decision needed, create context/decisions/[number]-[name].md
3. Update changelog.md with the change
4. Update AGENTS.md if needed - Ensure feature intent is in "Context Files to Load" section under "Feature-Specific Context"

Use these templates:

---
UPDATED FEATURE-[NAME].MD:
---
# Feature: [FEATURE_NAME]

## What
[Updated description - what this feature does now]

## Why
[Updated reasoning - why we need these changes]

## Success Criteria
- [Updated criterion 1]
- [Updated criterion 2]

## Changes from Original
- [What changed and why]

## Technical Approach
See: decisions/[decision-file].md

## Related
- Intent: project-intent.md
- Decision: [decision files]
- Related Features: [if any]

## Status
- **Created**: [ORIGINAL DATE] (Phase: Intent)
- **Updated**: [TODAY'S DATE] (Phase: Intent) - [reason for update]
- **Status**: In Progress
---

---
NEW DECISION (if needed) - DECISIONS/[NUMBER]-[NAME].MD:
---
# Decision: [CHANGE TITLE]

## Context
Updating [FEATURE_NAME] feature: [what triggered this change]

## Decision
[New technical approach or change]

## Rationale
[Why this change/approach was chosen]

## Alternatives
- [Alternative 1] - [why not chosen]
- [Alternative 2] - [why not chosen]

## Impact
- Affects: [what this impacts]
- Requires: [what needs to change]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
---

---
ADD TO CHANGELOG.MD:
---
## [Unreleased]

### Changed
- Feature: [FEATURE_NAME] - [what changed and why]
---

Update the files based on my answers. If a new technical decision is needed, create it before implementation.
```

---

## What This Prompt Does

- **Updates feature intent** - Reflects the new requirements
- **Creates decision if needed** - Documents new technical approach
- **Updates changelog** - Tracks the change
- **Maintains history** - Keeps track of what changed and why

---

## When to Use This Prompt

- Feature requirements changed
- User feedback requires changes
- Business needs evolved
- Scope of feature expanded or reduced
- Technical approach needs to change

---

## Execute: Build the Changes

After the context files are updated, use this simple prompt to build:

```
Now load the @context files and implement the changes.
```

The AI will:
1. Load updated feature intent and any new decisions
2. Generate code following the updated context
3. Implement the changes according to the updated intent

---

## After Using This Prompt

1. **Review updated intent** - Ensure changes are captured
2. **Check if ADR needed** - New approach = new decision
3. **Execute** - Use the execution prompt above to build

**Note**: The AI will automatically update context after implementation if you have AGENTS.md. If not, you can manually use `learn-update.md` prompt.

---

## Optional: Next Steps

- **Found a bug?** Use `fix-bug.md`

