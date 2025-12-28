# Prompt: Update Context (Learn Step)

Use this prompt after implementing to update context with outcomes and learnings.

**What is the Learn step?** The third step of Context Mesh (Intent → Build → **Learn**):
- Mark work as complete
- Record what actually happened vs planned
- Capture patterns and learnings for future work

> **Note:** If you have AGENTS.md configured, AI does this automatically. This prompt is for manual updates.

## How to Use

1. **Copy** the prompt below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** the questions
4. **Review** updates

---

## Prompt

```
I finished implementing and need to update the Context Mesh (Learn step).

Analyze @context/ and the implemented code, then ask me:

**Implementation Summary:**
1. What was implemented? (feature, bug fix, or change)
2. Which context files are related? (feature intent, decisions, etc.)
3. Did implementation follow the plan? (If not, what changed?)

**Outcomes and Learnings:**
4. What worked well? (what went as expected)
5. What didn't work as expected? (surprises, issues, trade-offs)
6. Any lessons learned? (insights for future work)
7. Did you discover a reusable pattern?
8. Did you discover something that doesn't work (anti-pattern)?

Then update:
- Mark feature/bug as complete in intent file (update Status)
- Add/update "Outcomes" section in decision file(s):
  - Format: "After Implementation" (what worked/didn't work)
  - Format: "Lessons Learned" (insights for future)
  - Update Status section: Add "Updated: [DATE] (Phase: Learn) - Added outcomes"
- Update changelog.md
- Create context/evolution/learning-[name].md if significant learning
- Create context/knowledge/patterns/[name].md if pattern discovered
- Create context/knowledge/anti-patterns/[name].md if anti-pattern discovered
- Update AGENTS.md if feature context changed significantly

Follow the pattern of existing files in @context/.
Remember: Outcomes should be specific and actionable, following the format in existing decision files.
```

---

## What This Prompt Does

- **Marks work as complete** - Updates status in intent files
- **Records outcomes** - What actually happened vs planned (formatted as "After Implementation" and "Lessons Learned")
- **Updates decision status** - Adds "Updated" date in Status section
- **Captures learnings** - Knowledge for future work
- **Updates changelog** - Records completion
- **Creates patterns** - Reusable knowledge
- **Updates AGENTS.md** - Keeps references current if context changed significantly

**Outcomes Format**: The prompt ensures outcomes follow the standard format:
- **After Implementation**: What worked ✅, what didn't ⚠️, what needs attention
- **Lessons Learned**: Actionable insights for future work
- **Status Update**: Records when outcomes were added (Phase: Learn)

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
