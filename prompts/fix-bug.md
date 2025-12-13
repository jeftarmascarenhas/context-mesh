# Prompt: Fix Bug

Use this prompt to document and fix a bug in your Context Mesh project.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer questions** about the bug
4. **Review** the generated files

---

## Prompt

```
I need to fix a bug in my project that uses Context Mesh.

Context Mesh workflow:
1. Intent - Document the bug and fix approach
2. Build - Implement the fix
3. Learn - Update context after fix is verified

Please help me create the context files for this bug fix.

Ask me:
1. What is the bug? (Brief description)
2. What is the expected behavior vs actual behavior?
3. What is the impact? (Critical, high, medium, low)
4. Do you know the root cause? (If yes, what is it?)
5. What is your fix approach?
6. Which feature does this bug affect?
7. Does this require a technical decision? (significant change to approach)

After I answer, create these files:

1. context/intent/bug-[name].md - The bug documentation
2. context/decisions/[number]-[name].md - Only if fix requires significant technical decision
3. Update changelog.md - Add the bug fix
4. Update AGENTS.md if needed - Ensure bug intents are mentioned in "Context Files to Load" section under "Feature-Specific Context"

Use these templates:

---
BUG-[NAME].MD TEMPLATE:
---
# Bug: [BUG_NAME]

## Description
[What the bug is - clear description]

## Expected vs Actual
- **Expected**: [What should happen]
- **Actual**: [What actually happens]

## Impact
- **Severity**: [Critical / High / Medium / Low]
- **Affected**: [What features/users are affected]

## Root Cause
[Root cause if known, or "To be investigated"]

## Fix Approach
[How the bug will be fixed]

## Success Criteria
- [ ] Bug no longer occurs
- [ ] Expected behavior works correctly
- [ ] No regression in related features
- [ ] Test added to prevent recurrence

## Related
- Feature: [affected feature].md
- Decision: [if applicable]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Draft
---

---
DECISION (only if significant change needed) - DECISIONS/[NUMBER]-[NAME].MD:
---
# Decision: [FIX APPROACH TITLE]

## Context
Fixing bug: [BUG_NAME]
Root cause: [root cause]

## Decision
[Technical approach to fix]

## Rationale
[Why this approach was chosen]

## Alternatives
- [Alternative 1] - [why not chosen]

## Status
- **Created**: [TODAY'S DATE] (Phase: Intent)
- **Status**: Accepted
---

---
ADD TO CHANGELOG.MD:
---
## [Unreleased]

### Fixed
- Bug: [BUG_NAME] - [brief description of fix]
---

Create the files based on my answers.
```

---

## What This Prompt Does

- **Documents the bug** - Clear description and impact
- **Records root cause** - If known
- **Documents fix approach** - How it will be fixed
- **Creates decision if needed** - For significant changes
- **Updates changelog** - Tracks the fix

---

## When to Use This Prompt

- Found a bug that needs fixing
- User reported an issue
- Test revealed unexpected behavior
- Production incident occurred

---

## Execute: Fix the Bug

After the bug is documented, use this simple prompt to fix:

```
Now load the @context files and fix the bug.
```

The AI will:
1. Load bug intent, any related decisions, and affected feature intents
2. Generate code following the fix approach
3. Implement the fix according to the bug documentation

---

## After Using This Prompt

1. **Review bug documentation** - Ensure it's clear
2. **Execute** - Use the execution prompt above to fix
3. **Add tests** - Prevent recurrence

**Note**: The AI will automatically update context after implementation if you have AGENTS.md. If not, you can manually use `learn-update.md` prompt.

---

## Optional: Next Steps

- Continue with next feature or bug fix

