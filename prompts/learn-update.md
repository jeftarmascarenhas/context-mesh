# Prompt: Update Context (Learn Step)

Use after implementing to keep context current.

**Note:** If you have AGENTS.md configured, AI does this automatically. This prompt is for manual updates.

---

## Prompt

```
I finished implementing and need to update the Context Mesh (Learn step).

Analyze @context/ and the implemented code, then ask me:
1. What was implemented? (feature, bug fix, or change)
2. Which context files are related?
3. Did implementation follow the plan? (If not, what changed?)
4. Any learnings or insights?
5. Did you discover a reusable pattern?
6. Did you discover something that doesn't work (anti-pattern)?

Then update:
- Mark feature/bug as complete in intent file
- Add "Outcomes" section in decision file
- Update changelog.md
- Create context/evolution/learning-[name].md if significant learning
- Create context/knowledge/patterns/[name].md if pattern discovered
- Create context/knowledge/anti-patterns/[name].md if anti-pattern discovered

Follow the pattern of existing files in @context/.
```

---

## What This Prompt Does

- **Marks work as complete** - Updates status in intent files
- **Records outcomes** - What actually happened vs planned
- **Captures learnings** - Knowledge for future work
- **Updates changelog** - Records completion
- **Creates patterns** - Reusable knowledge

---

## Context Mesh Cycle

This prompt completes the 3-step cycle:

```
Intent → Build → Learn
  ↑                 │
  └─────────────────┘
```

After Learn, start a new cycle with:
- `add-feature.md` - New feature
- `update-feature.md` - Update feature
- `fix-bug.md` - Fix bug
