# Prompt: Update Feature

Use this prompt to update an existing feature in a project with Context Mesh.

**When to use?** When you need to change an already implemented feature:
- New requirements
- Changed scope
- Different technical approach

**Important**: You can use this prompt even if the feature is already built and deployed. This is Step 1 (Intent) - it plans the changes before implementing them.

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

First, analyze the existing @context/ files (feature intents, decisions) to understand the current state.

Then ask me:

**Feature Update:**
1. Which feature is being updated? (name or file)
2. What is changing?
3. Why is this change needed?
4. Do acceptance criteria change?

**Technical Decision:**
5. Does this need a new technical decision? (different approach)
   - If YES, ask:
     - Technical approach - What technical solution will be used?
     - Why this approach? (Rationale) - What are the reasons for choosing this approach?
     - What alternatives did you consider? - What other options were evaluated and why weren't they chosen?
     - Technical context - Any constraints, existing patterns, or dependencies that influence this decision?
6. Does the existing decision need to be updated? (same approach, but rationale/outcomes changed)
   - If YES, ask what needs to be updated in the existing decision

Then:
- Update context/intent/feature-[name].md with changes
  - Add "Changes from Original" section if relevant
  - Update "Related" section if links changed (ensure bidirectional links to decision files)
- Create context/decisions/[next-number]-[name].md if new technical approach
  - Include: Context, Decision, Rationale, Alternatives Considered, Related links, Status
  - Include "Related" section with bidirectional links:
    - [Project Intent](../intent/project-intent.md)
    - [Feature: [Feature Name]](../intent/feature-[name].md)
    - [Decision: Tech Stack](001-tech-stack.md) (if applicable)
- Update context/decisions/[existing-number]-[name].md if existing decision needs changes
  - Update "Related" section if links changed (ensure bidirectional links to feature files)
- Update changelog.md
- Update AGENTS.md (Feature-Specific Context section) if feature context changed

**Important**: Maintain bidirectional links between feature and decision files:
- Feature files must link to their decision files using format: `- [Decision: Name](../decisions/[number]-[name].md)`
- Decision files must link back to their feature files using format: `- [Feature: Name](../intent/feature-[name].md)`
- Use markdown link format: `- [Type: Name](path/to/file.md)`

Follow the pattern of existing files in @context/.
Remember: If creating a new decision, it should be complete with all sections (same quality as add-feature.md).
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
- **Creates complete decision if needed** - New technical approach with context, rationale, and alternatives
- **Updates existing decision if needed** - Updates rationale, outcomes, or other sections
- **Updates changelog** - Records the change
- **Updates AGENTS.md** - Keeps references current if feature context changed
- **Preserves history** - Documents what changed and why

**Decision Quality**: If creating a new decision, the prompt collects all necessary information (same as add-feature.md):
- Context (situation and requirements)
- Decision (technical approach details)
- Rationale (why this approach)
- Alternatives Considered (other options evaluated)
- Related links (to features, other decisions, etc.)

---

## Next Steps

- **Found a bug?** Use `fix-bug.md`
- **Done implementing?** AI updates context automatically (if AGENTS.md exists) or use `learn-update.md`
