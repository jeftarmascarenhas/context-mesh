# Prompt: Update Feature

Copy → Paste in AI → Answer → Files updated

---

## Prompt

```
I need to update an existing feature in this Context Mesh project.

Analyze the existing @context/ and ask me:
1. Which feature is being updated? (name or file)
2. What is changing?
3. Why is this change needed?
4. Do success criteria change?
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
Implement the changes following @context/intent/feature-[name].md
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
