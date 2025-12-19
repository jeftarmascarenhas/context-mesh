# Prompt: Update Feature

Use this prompt to update an existing feature in a project with Context Mesh.

**When to use?** When you need to change an already implemented feature:
- New requirements
- Changed scope
- Different technical approach

**Important**: Update the same `feature-*.md` file (don't create feature-v2.md). Git preserves history. Only create a new file if it's a completely different feature or complete replacement.

## How to Use

1. **Copy** the prompt below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** the questions
4. **Review** updated files
5. **Implement** - Use the execution prompt to make changes

---

## Prompt

```
I need to update an existing feature in this Context Mesh project.

Analyze the existing @context/ and ask me:
1. Which feature is being updated? (name or file)
2. What is changing?
3. Why is this change needed?
4. Do acceptance criteria change?
5. Does this need a new technical decision?

Then:
- Update context/intent/feature-[name].md with changes
- Create context/decisions/[next-number]-[name].md if new technical approach
- Update changelog.md

Follow the pattern of existing files in @context/.
Add "Changes from Original" section in intent if relevant.
```

---

## Execute: Implement Changes

After files are updated:

```
Update the existing feature following @context/intent/feature-[name].md.

IMPORTANT: This is an UPDATE to existing code, not a new implementation.
- First, analyze the existing code for this feature
- Identify what needs to change based on the updated intent
- Make ONLY the necessary modifications
- Preserve existing code that doesn't need to change
- Follow the "Changes from Original" section if present in the intent file
- Update only the files that need changes, don't regenerate everything
```

---

## What This Prompt Does

- **Updates feature intent** - Reflects new requirements
- **Creates decision if needed** - New technical approach
- **Updates changelog** - Records the change
- **Preserves history** - Documents what changed and why

---

## Next Steps

- **Found a bug?** Use `fix-bug.md`
- **Done implementing?** AI updates context automatically (if AGENTS.md exists) or use `learn-update.md`
