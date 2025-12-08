# Prompt: Initialize Context Mesh for Freelance/Client Project

Use this prompt when starting a freelance or client project. This helps you document client requirements clearly and maintain context throughout delivery.

## How to Use

1. Copy the prompt below
2. Paste it in your AI assistant (Cursor, Copilot, Claude, etc.)
3. Answer questions about the client project
4. Paste the client brief/requirements when asked
5. Review and refine the generated structure

---

## Prompt

```
I'm starting a freelance/client project and want to use Context Mesh to:
1. Document client requirements clearly
2. Track technical decisions
3. Maintain context throughout the project
4. Deliver maintainable code

Context Mesh structure:
- context/intent/ - What and why (project-intent.md, feature-*.md)
- context/decisions/ - Technical decisions (001-*.md, 002-*.md, ...)
- context/knowledge/patterns/ - Coding patterns
- context/knowledge/anti-patterns/ - Patterns to avoid
- context/evolution/ - Changelog and learnings (changelog.md)

Please help me set this up by asking me questions, then create the complete structure.

Start by asking:
1. What is the client/project name?
2. What type of project is it? (website, web app, mobile app, API, etc.)
3. Do you have a client brief or requirements document? (If yes, ask me to paste it)
4. What are the main deliverables/features requested?
5. What is the timeline/deadline?
6. Are there any specific technology requirements or constraints?
7. What are the acceptance criteria? (How will the client know it's done?)

After I provide the information (especially the client brief), create:
1. Complete context/ directory structure
2. context/intent/project-intent.md with:
   - What: Project description based on client brief
   - Why: Client's business needs and goals
   - Success Criteria: Deliverables and acceptance criteria
3. context/intent/feature-*.md files for each main feature/deliverable mentioned
4. context/decisions/ folder (will be populated as you make technical decisions)
5. context/evolution/changelog.md initialized with project start
6. Optionally, AGENTS.md for project setup and workflow

For each feature intent, include:
- What: What needs to be built
- Why: Why the client needs it (business value)
- Success Criteria: How to know it's complete
- Status: Created date and Draft status

Make sure all files follow Context Mesh format with proper Status sections.
```

---

## What This Prompt Does

- **Captures client requirements** - Documents what the client wants
- **Creates feature intents** - One intent file per deliverable/feature
- **Sets up decision tracking** - Ready for technical decisions as you build
- **Documents acceptance criteria** - Clear success criteria for each feature
- **Maintains project context** - Helps you remember decisions throughout delivery

---

## After Using This Prompt

1. **Review with client** - Ensure project-intent.md matches their expectations
2. **Refine feature intents** - Add more detail as you clarify requirements
3. **Document decisions** - Create decision files as you make technical choices
4. **Update as you build** - Follow Intent → Build → Learn workflow
5. **Track learnings** - Document what works/doesn't work in evolution/

---

## Tips

- **Get client approval** - Share project-intent.md with client to ensure alignment
- **Update feature intents** - Refine as requirements become clearer
- **Document all decisions** - Especially important for client projects
- **Track changes** - Use changelog.md to document scope changes
- **Learn continuously** - Document learnings that might help future projects

---

## For Projects with Existing Briefs

If you already have a detailed brief, you can paste it directly:

```
I have a client brief. Here it is:

[PASTE CLIENT BRIEF HERE]

Please create the Context Mesh structure based on this brief, asking me 
clarifying questions only if something is unclear.
```

