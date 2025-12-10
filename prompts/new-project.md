# Prompt: Initialize Context Mesh for New Project

Use this prompt when starting a brand new project from scratch. This prompt will guide you through creating the Context Mesh structure interactively.

## How to Use

1. Copy the prompt below
2. Paste it in your AI assistant (Cursor, Copilot, Claude, etc.)
3. Answer the questions as the AI asks them
4. Review and refine the generated structure

---

## Prompt

```
I'm starting a new project and want to initialize Context Mesh to help maintain 
context throughout development.

Context Mesh is a framework that organizes project context into:
- context/intent/ - What and why (project-intent.md, feature-*.md, bug-*.md)
- context/decisions/ - Technical decisions (001-*.md, 002-*.md, ...)
- context/knowledge/patterns/ - Coding patterns
- context/knowledge/anti-patterns/ - Patterns to avoid
- context/evolution/ - Changelog and learnings (changelog.md, learning-*.md)

Please help me set this up by asking me questions about my project, then create 
the complete Context Mesh structure.

Start by asking me:
1. What is the project name?
2. What type of project is it? (web app, API, mobile app, CLI tool, library, etc.)
3. What is the main purpose of this project? (What problem does it solve?)
4. Why is this project important? (Business value, personal learning, etc.)
5. What are the main features or capabilities you plan to build?
6. What technology stack are you planning to use? (if known)
7. What are the success criteria? (How will you know the project is successful?)

After I answer, create:
1. The complete context/ directory structure with all subdirectories
2. context/intent/project-intent.md with What, Why, and Success Criteria based on my answers
3. context/evolution/changelog.md initialized with the project start
4. Optionally, context/intent/feature-*.md files for each main feature I mentioned
5. Optionally, a basic AGENTS.md file that references the context files

Make sure all files follow Context Mesh format with proper Status sections.
```

---

## What This Prompt Does

- **Asks questions interactively** - Guides you through providing project information
- **Creates complete structure** - Sets up all necessary directories and initial files
- **Generates project-intent.md** - Creates your main intent document from your answers
- **Sets up feature intents** - Creates feature intent files for main features
- **Creates AGENTS.md** - Optional router file for AI agents

---

## After Using This Prompt

1. **Review generated files** - Check that project-intent.md accurately reflects your vision
2. **Add more details** - Expand feature intents or add technical decisions as needed
3. **Start building** - Use the context files to guide AI-assisted development
4. **Update as you learn** - Follow the Intent → Build → Learn workflow

---

## Tips

- **Be specific in answers** - More detail helps create better context
- **You can refine later** - Start minimal, add details as you build
- **Update continuously** - Context Mesh is a living structure that evolves with your project


