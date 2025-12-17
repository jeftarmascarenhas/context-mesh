# Prompt: Add Feature

Copy → Paste in AI → Answer → Files created

---

## Prompt

```
Add a new feature to this Context Mesh project.

Analyze the existing @context/ and ask me:
1. Feature name
2. What it does and why we need it
3. Success criteria
4. Technical approach (becomes the decision/ADR)

Then create:
- context/intent/feature-[name].md
- context/decisions/[next-number]-[name].md (ADR required BEFORE implementing)
- Update changelog.md
- Update AGENTS.md (Feature-Specific Context section)

Follow the pattern of existing files in @context/.
Remember: ADR must exist before implementation starts.
```

---

## Execute: Build the Feature

After files are created:

```
Implement the feature following @context/intent/feature-[name].md 
and @context/decisions/[number]-[name].md
```

---

## What This Prompt Does

- **Creates feature intent** - Documents what and why
- **Creates decision (ADR)** - Documents technical approach (required before implementation)
- **Updates changelog** - Records the new feature
- **Updates AGENTS.md** - Keeps references current

---

## Next Steps

- **Feature changed?** Use `update-feature.md`
- **Found a bug?** Use `fix-bug.md`
- **Done implementing?** AI updates context automatically (if AGENTS.md exists) or use `learn-update.md`
