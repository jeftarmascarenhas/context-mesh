# Prompt: Update Context After Implementation (Learn Step)

Use this prompt after implementing a feature, fix, or change to update your Context Mesh.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer questions** about what was implemented
4. **Review** the updated files

---

## Prompt

```
I just finished implementing something and need to update my Context Mesh (Learn step).

Context Mesh Learn step:
- Update context to reflect what was actually implemented
- Update decision outcomes (what actually happened)
- Document learnings
- Update changelog
- Mark features/bugs as complete

Please help me update the context files.

Ask me:
1. What did you just implement? (feature, bug fix, or change)
2. Which context files are related? (feature-*.md, bug-*.md, decision-*.md)
3. Did the implementation match the plan? (Yes/No, if no, what changed?)
4. Any learnings or insights? (What worked well, what was harder than expected)
5. Any new patterns discovered? (Reusable approaches)
6. Any anti-patterns to avoid? (Things that didn't work)

After I answer, update these files:

1. Update the feature/bug intent file - Mark as completed, add implementation notes
2. Update decision file - Add outcomes section
3. Update changelog - Move from Unreleased to version or mark as completed
4. Create learning file (if significant learnings)
5. Create pattern/anti-pattern file (if applicable)

Use these templates:

---
UPDATED FEATURE/BUG FILE (mark as complete):
---
## Status
- **Created**: [ORIGINAL DATE] (Phase: Intent)
- **Updated**: [TODAY'S DATE] (Phase: Learn)
- **Status**: Completed

## Implementation Notes
[What was actually implemented, any deviations from plan]

## Learnings
[What was learned during implementation]
---

---
UPDATED DECISION FILE (add outcomes):
---
## Outcomes
(Added in Learn phase after implementation)

### What Happened
- [Actual result 1]
- [Actual result 2]

### Performance
- [Any metrics or observations]

### Learnings
- [What we learned from this decision]
---

---
LEARNING FILE (if significant) - EVOLUTION/LEARNING-[NAME].MD:
---
# Learning: [LEARNING_TITLE]

## Context
[What we were doing when we learned this]

## Insight
[What we learned]

## Impact
[How this affects future work]

## Action
[What we'll do differently]

## Related
- Feature/Bug: [related file]
- Decision: [related decision]

## Status
- **Created**: [TODAY'S DATE] (Phase: Learn)
- **Status**: Active
---

---
PATTERN FILE (if discovered) - KNOWLEDGE/PATTERNS/[NAME].MD:
---
# Pattern: [PATTERN_NAME]

## Description
[What this pattern is]

## When to Use
[When to apply this pattern]

## Example
[Code or approach example]

## Benefits
- [Benefit 1]
- [Benefit 2]

## Status
- **Created**: [TODAY'S DATE]
- **Status**: Active
---

---
ANTI-PATTERN FILE (if discovered) - KNOWLEDGE/ANTI-PATTERNS/[NAME].MD:
---
# Anti-Pattern: [ANTI_PATTERN_NAME]

## Description
[What to avoid]

## Why It's Bad
[Why this doesn't work]

## What to Do Instead
[Better approach]

## Status
- **Created**: [TODAY'S DATE]
- **Status**: Active
---

---
UPDATED CHANGELOG.MD:
---
## [Version or Date]

### Added
- [Feature name] - [description]

### Changed
- [What changed]

### Fixed
- [Bug name] - [description]

### Learned
- [Key learning]
---

Update the files based on my answers. This completes the Context Mesh cycle for this work item.
```

---

## What This Prompt Does

- **Marks work as complete** - Updates status in intent files
- **Records outcomes** - What actually happened vs what was planned
- **Captures learnings** - Knowledge for future work
- **Updates changelog** - Records the completion
- **Creates patterns** - Reusable knowledge for the team

---

## When to Use This Prompt

- Just finished implementing a feature
- Just fixed a bug
- Just completed a refactoring
- Any time you complete work and want to capture learnings

---

## After Using This Prompt

1. **Review updates** - Ensure context reflects reality
2. **Share learnings** - With team if applicable
3. **Start next item** - Return to Intent step for new work

---

## Context Mesh Cycle

This prompt completes the 3-step cycle:

```
Intent → Build → Learn
  ↑                 │
  └─────────────────┘
```

After Learn, you can start a new cycle with:
- `add-feature.md` - For new features
- `update-feature.md` - For feature changes
- `fix-bug.md` - For bugs

