# Prompt: Fix Bug

Use this prompt to document and fix a bug in a project with Context Mesh.

**Why document bugs?** Tracking bugs in context preserves:
- What went wrong and why
- Root cause analysis
- How it was fixed (prevents similar bugs)

## How to Use

1. **Copy** the prompt below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** the questions
4. **Review** generated files
5. **Fix** - Use the execution prompt to fix the bug

---

## Prompt

```
I need to fix a bug in this Context Mesh project.

**FIRST: Load framework context:**
- Load @context/.context-mesh-framework.md (if exists) to understand Context Mesh framework rules and file type separation
- Understand Plan, Approve, Execute pattern
- Understand when to create vs not create files

Then, analyze the existing @context/ and ask me:
1. What is the bug? (brief description)
2. Expected vs actual behavior
3. Impact (critical, high, medium, low)
4. Root cause (if known)
5. Which feature is affected?

Then create:
- context/intent/bug-[name].md
- context/decisions/[next-number]-[name].md (only if fix requires significant technical change)
- Update changelog.md

Follow the pattern of existing files in @context/.
```

---

## Execute: Fix the Bug

After files are created, use this prompt to fix:

```
Fix the bug following @context/intent/bug-[name].md

**MANDATORY: Follow Plan, Approve, Execute pattern:**

1. **PLAN** (Do this first - DO NOT SKIP):
   - Load @context/.context-mesh-framework.md (if exists) to understand framework rules
   - Load @context/intent/project-intent.md (always)
   - Load @context/intent/bug-[name].md
   - Load @context/decisions/[number]-[name].md (if bug fix requires technical decision)
   - Load relevant patterns from @context/knowledge/patterns/ (if any)
   - Analyze existing code to understand the bug
   - Identify root cause (if documented in bug file)
   - Explain your approach to fix the bug
   - List ALL files you will modify
   - Explain how the fix addresses the root cause
   - Present the complete plan clearly

2. **APPROVE** (Wait for approval - DO NOT SKIP):
   - Ask explicitly: "Should I proceed with this bug fix plan?"
   - DO NOT write any code until user approves
   - If user requests changes, update plan and ask again

3. **EXECUTE** (Only after approval):
   - Implement the fix according to approved plan
   - Follow all context files strictly
   - Ensure the fix addresses the root cause
   - Test that the fix resolves the issue
```

---

## What This Prompt Does

- **Documents the bug** - Clear description and impact
- **Records root cause** - If known
- **Creates decision if needed** - Only for significant technical changes
- **Updates changelog** - Records the fix

---

## Next Steps

- **Done fixing?** AI updates context automatically (if AGENTS.md exists) or use `learn-update.md`
- **New feature?** Use `add-feature.md`
