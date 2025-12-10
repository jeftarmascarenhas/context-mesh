# Prompt: Add Context Mesh to Existing Project

Use this prompt when you have an existing project and want to add Context Mesh to it. This prompt will analyze your codebase and create the Context Mesh structure based on what already exists.

## How to Use

1. Copy the prompt below
2. Paste it in your AI assistant (Cursor, Copilot, Claude, etc.)
3. The AI will analyze your codebase structure
4. Review and refine the generated context files

---

## Prompt

```
I have an existing project and want to add Context Mesh to help maintain 
context going forward. Please analyze my current codebase and create a Context 
Mesh structure that documents what already exists.

Context Mesh structure:
- context/intent/ - What and why (project-intent.md, feature-*.md)
- context/decisions/ - Technical decisions (001-*.md, 002-*.md, ...)
- context/knowledge/patterns/ - Coding patterns found in codebase
- context/knowledge/anti-patterns/ - Patterns to avoid
- context/evolution/ - Changelog and learnings (changelog.md)

Please:
1. Analyze the current project structure (directories, files, configuration)
2. Identify the main technologies and frameworks used
3. Identify key features/modules by examining the codebase
4. Identify common patterns in the code
5. Extract technical decisions from code structure and configuration

Then create:
1. Complete context/ directory structure
2. context/intent/project-intent.md describing:
   - What the project currently does (based on codebase analysis)
   - Why it exists (infer from structure and code)
   - Current success criteria
3. context/decisions/ files for key technical choices:
   - Tech stack decisions (from package.json, requirements.txt, etc.)
   - Architecture decisions (from project structure)
   - Database/API design decisions (from code patterns)
   - Framework/library choices
4. context/knowledge/patterns/ files for common patterns you identify
5. context/evolution/changelog.md initialized with current state
6. Optionally, AGENTS.md that:
   - References context files
   - Documents setup commands (from package.json, README, etc.)
   - Describes project structure

For each decision file, include:
- Context: What was the situation?
- Decision: What was chosen?
- Rationale: Why was it chosen? (infer from code patterns)
- Alternatives: What else could have been used?

Make sure all files follow Context Mesh format with proper Status sections.
```

---

## What This Prompt Does

- **Analyzes codebase** - Examines project structure, dependencies, and code patterns
- **Extracts intent** - Infers project purpose from existing code
- **Documents decisions** - Creates decision files for technical choices already made
- **Identifies patterns** - Documents coding patterns found in the codebase
- **Creates complete structure** - Sets up all Context Mesh directories and files

---

## After Using This Prompt

1. **Review extracted context** - Verify that the AI correctly understood your project
2. **Refine decisions** - Add more rationale or alternatives if needed
3. **Add missing patterns** - Document any patterns the AI might have missed
4. **Start using** - Use the context files going forward for new development

---

## Tips

- **Review carefully** - AI inference may not be 100% accurate
- **Add missing context** - Fill in any gaps in the generated files
- **Update as you build** - Use Context Mesh for all new features and decisions
- **Document learnings** - Add to evolution/ as you discover new patterns

---

## For Large Codebases

If your project is very large, you can be more specific:

```
Focus on analyzing:
- [specific directories or modules]
- [specific technologies or frameworks]
- [specific features you want to document first]
```

This helps the AI focus on the most important parts first.


