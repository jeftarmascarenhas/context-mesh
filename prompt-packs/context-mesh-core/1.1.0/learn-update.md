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
3. **Review** the AI's automatic analysis (it will analyze code and context first)
4. **Answer** only the subjective questions (what worked well, surprises, lessons)
5. **Review** the final updates

---

## Prompt

```
I finished implementing and need to update the Context Mesh (Learn step).

**FIRST: Load framework context:**
- Load @context/.context-mesh-framework.md (if exists) to understand Context Mesh framework rules
- Understand the Learn step purpose and what needs to be updated
- Understand file type separation rules

**THEN: Analyze automatically (do not ask questions yet):**

1. **Analyze @context/** to identify:
   - Which feature/bug intent files exist and their status
   - Which decision files are related to recent work
   - What was planned (from intent and decision files)

2. **Analyze the codebase** to identify:
   - What code was actually implemented (new files, modified files, recent changes)
   - Compare implementation with the plan (from context files)
   - Identify differences between plan and actual implementation

3. **Match implementation to context:**
   - Which feature/bug does the code correspond to?
   - Which decision files are relevant?
   - Did implementation follow the documented decisions?

**THEN: Present your analysis and ask only for subjective insights:**

Present your findings:
- ✅ What was implemented (based on code analysis)
- ✅ Which context files are related (based on code and context matching)
- ✅ Implementation vs Plan comparison (what matches, what differs)
- ✅ Technical observations (what you can see from the code)

**Ask only for insights I need to provide:**
1. What worked well? (subjective experience - what went smoothly)
2. What didn't work as expected? (surprises, issues, trade-offs you encountered)
3. Any lessons learned? (insights for future work)
4. Did you discover a reusable pattern? (if yes, describe it)
5. Did you discover something that doesn't work (anti-pattern)? (if yes, describe it)

**Then update automatically:**
- Mark feature/bug as complete in intent file (update Status)
- Add/update "Outcomes" section in decision file(s):
  - Format: "After Implementation" (what worked ✅, what didn't ⚠️, based on code analysis + my insights)
  - Format: "Lessons Learned" (insights for future)
  - Update Status section: Add "Updated: [DATE] (Phase: Learn) - Added outcomes"
- Update changelog.md with what was implemented
- Create context/evolution/learning-[name].md if significant learning
- Create context/knowledge/patterns/[name].md if pattern discovered
- Create context/knowledge/anti-patterns/[name].md if anti-pattern discovered
- Update AGENTS.md if feature context changed significantly

Follow the pattern of existing files in @context/.
Remember: Outcomes should be specific and actionable, following the format in existing decision files.
```

---

## What This Prompt Does

- **Analyzes code automatically** - Compares implemented code with context files to identify what was built
- **Identifies related context** - Matches code to feature intents and decisions automatically
- **Compares plan vs reality** - Highlights differences between documented plan and actual implementation
- **Marks work as complete** - Updates status in intent files
- **Records outcomes** - What actually happened vs planned (formatted as "After Implementation" and "Lessons Learned")
- **Updates decision status** - Adds "Updated" date in Status section
- **Captures learnings** - Knowledge for future work
- **Updates changelog** - Records completion
- **Creates patterns** - Reusable knowledge
- **Updates AGENTS.md** - Keeps references current if context changed significantly

**Analysis Approach**: The prompt instructs AI to:
1. **Analyze first** - Read context files and codebase to understand what was planned and what was built
2. **Present findings** - Show what was discovered automatically
3. **Ask selectively** - Only ask for subjective insights that require human input (what worked well, surprises, lessons)

**Outcomes Format**: The prompt ensures outcomes follow the standard format:
- **After Implementation**: What worked ✅, what didn't ⚠️, what needs attention (based on code analysis + user insights)
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
