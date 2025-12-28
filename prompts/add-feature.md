# Prompt: Add Feature

Use this prompt to add a new feature to a project that already has Context Mesh.

**What is a feature?** A distinct piece of functionality (e.g., "user authentication", "payment processing", "dark mode"). Each feature gets:
- **Intent file** (`feature-*.md`) - Documents WHAT and WHY
- **Decision file** (`decisions/*.md`) - Documents HOW (technical approach, also called ADR)

## How to Use

1. **Copy** the prompt below
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** the questions
4. **Review** generated files
5. **Build** - Use the execution prompt to implement

---

## Prompt

```
Add a new feature to this Context Mesh project.

Analyze the existing @context/ and ask me:

**Feature Information:**
1. Feature name
2. What it does and why we need it
3. Acceptance criteria

**Technical Decision (ADR):**
4. Technical approach - What technical solution will be used?
5. Why this approach? (Rationale) - What are the reasons for choosing this approach?
6. What alternatives did you consider? - What other options were evaluated and why weren't they chosen?
7. Technical context - Any constraints, existing patterns, or dependencies that influence this decision?

Then create:
- context/intent/feature-[name].md
- context/decisions/[next-number]-[name].md (ADR required BEFORE implementing)
  - Include: Context, Decision, Rationale, Alternatives Considered, Related links, Status
- Update changelog.md
- Update AGENTS.md (Feature-Specific Context section)

Follow the pattern of existing files in @context/.
Remember: ADR must exist before implementation starts. The decision file should be complete with all sections.
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
- **Creates complete decision (ADR)** - Documents technical approach with context, rationale, and alternatives (required before implementation)
- **Updates changelog** - Records the new feature
- **Updates AGENTS.md** - Keeps references current

**Decision Quality**: The prompt collects all necessary information to create a complete ADR with:
- Context (situation and requirements)
- Decision (technical approach details)
- Rationale (why this approach)
- Alternatives Considered (other options evaluated)
- Related links (to features, other decisions, etc.)

---

## Next Steps

- **Feature changed?** Use `update-feature.md`
- **Found a bug?** Use `fix-bug.md`
- **Done implementing?** AI updates context automatically (if AGENTS.md exists) or use `learn-update.md`
