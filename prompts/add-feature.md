# Prompt: Add Feature to Existing Context Mesh Project

Use this prompt when you want to add a new feature to a project that already uses Context Mesh. This helps you create the proper context files for the new feature.

## How to Use

1. Copy the prompt below
2. Paste it in your AI assistant (Cursor, Copilot, Claude, etc.)
3. Answer questions about the new feature
4. Review the generated context files

---

## Prompt

```
I'm adding a new feature to my project that already uses Context Mesh. 
Please help me create the proper context files for this feature.

Context Mesh structure for features:
- context/intent/feature-[name].md - Feature intent (What, Why, Success Criteria)
- context/decisions/ - Technical decisions (if needed for this feature)
- Update context/intent/project-intent.md if this feature changes project scope

Please ask me questions about the feature, then create the appropriate context files.

Ask me:
1. What is the feature name?
2. What does this feature do? (What problem does it solve?)
3. Why are we building this feature? (Business value, user need, etc.)
4. What are the success criteria? (How will we know it's complete?)
5. Does this feature relate to any existing features? (If yes, which ones?)
6. Are there any technical decisions needed? (e.g., authentication approach, database design, API design)
7. Does this feature change the overall project scope or goals?

After I answer, create:
1. context/intent/feature-[feature-name].md with:
   - What: Feature description
   - Why: Business value and importance
   - Success Criteria: Measurable outcomes
   - Related: Links to related features (if any)
   - Status: Created date and Draft status
2. If technical decisions are needed, create context/decisions/[number]-[decision-name].md files
3. If project scope changes, update context/intent/project-intent.md accordingly

Make sure all files follow Context Mesh format with proper Status sections.
```

---

## What This Prompt Does

- **Creates feature intent** - Documents what the feature does and why
- **Identifies decisions needed** - Helps you think about technical choices
- **Links to existing context** - Connects new feature to existing features
- **Updates project scope** - Adjusts project-intent.md if needed
- **Maintains consistency** - Follows Context Mesh format

---

## After Using This Prompt

1. **Review feature intent** - Ensure it accurately describes what you want to build
2. **Create decisions** - If the prompt identified decisions needed, create those files
3. **Start building** - Use the feature intent to guide development
4. **Update as you build** - Follow Intent → Build → Learn workflow
5. **Document learnings** - Add to evolution/ after implementation

---

## Tips

- **Be specific** - Clear feature description helps with implementation
- **Link related features** - Helps maintain context relationships
- **Create decisions early** - Document technical choices before building
- **Update project intent** - Keep it aligned with project evolution
- **Track learnings** - Document what works/doesn't work after building

---

## For Complex Features

If the feature is complex, you can ask the AI to break it down:

```
This feature is complex. Please:
1. Break it down into smaller sub-features
2. Create feature intent files for each sub-feature
3. Link them together in a parent feature intent
```

This helps manage large features with proper context structure.

