# Prompt: Fix Bug

Copy → Paste in AI → Answer → Files created

---

## Prompt

```
I need to fix a bug in this Context Mesh project.

Analyze the existing @context/ and ask me:
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

After files are created:

```
Fix the bug following @context/intent/bug-[name].md
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
