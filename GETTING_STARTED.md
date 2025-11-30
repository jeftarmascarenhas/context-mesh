# Getting Started with Context Mesh

This guide will help you get started with Context Mesh in your project.

## Prerequisites

Before starting with Context Mesh, ensure you have:

- A development project (new or existing)
- Git repository (recommended)
- AI development tools (Cursor, GitHub Copilot, etc.)
- Team familiar with Agile/Scrum concepts (helpful but not required)

## Quick Start (5 Minutes)

### Step 1: Understand the Framework

Read the [FRAMEWORK.md](FRAMEWORK.md) to understand the 3-step workflow.

### Step 2: Initialize Context

Create a `context/` directory in your project:

```bash
mkdir -p context/{intent,decisions,knowledge/{patterns,anti-patterns},evolution}
```

### Step 3: Start with Intent

Create your first intent document:

```bash
cat > context/intent/initial-intent.md << 'EOF'
# Project Intent

## What
[Describe what you want to build]

## Why
[Why is this important?]

## Success Criteria
- [Criterion 1]
- [Criterion 2]
EOF
```

### Step 4: Follow the Workflow

Proceed through the 3 steps:
1. Intent ✅ (you just did this)
2. Build
3. Learn

## Detailed Setup

### 1. Project Structure

Create the following directory structure:

```
your-project/
├── context/
│   ├── intent/
│   │   ├── project-intent.md
│   │   ├── feature-*.md
│   │   ├── bug-*.md
│   │   └── refactor-*.md
│   ├── decisions/
│   │   └── 001-*.md, 002-*.md, ...
│   ├── knowledge/
│   │   ├── patterns/
│   │   └── anti-patterns/
│   └── evolution/
│       ├── changelog.md
│       └── learning-*.md
└── [your code]
```

### 2. Context Management

You can use simple markdown files or any documentation system. The key is to:
- Keep context simple and focused
- Update context continuously
- Link everything to intent
- Version control your context (using Git)

## Step-by-Step Implementation

### Step 1: Intent

**Objective**: Capture intent and initialize living context.

**Activities**:

1. **Define Intent** (can be initial or refined):
   ```markdown
   # Intent Statement
   
   ## What
   [What do you want to build?]
   
   ## Why
   [Why is this important?]
   
   ## Success Criteria
   - [Criterion 1]
   - [Criterion 2]
   ```

2. **Identify or Define Patterns** (for existing/new projects):
   - **Existing projects**: Identify existing patterns in codebase
   - **New projects**: Define initial patterns based on team experience
   - Store in `context/knowledge/patterns/`

3. **Create Initial Context**:
   - Store intent in your context repository
   - Link to project structure
   - Make it accessible to AI tools

**Checklist** (Definition of Done):
- [ ] Intent statement clear and validated (What + Why)
- [ ] Initial patterns identified (existing) or defined (new)
- [ ] Initial context created and stored
- [ ] Stakeholders aligned on intent

**Tips**:
- Keep intent simple and focused
- Make intent measurable
- Align with stakeholders early

---

### Step 2: Build

**Objective**: AI builds with context, human supervises, and decisions are documented.

**Activities**:

1. **AI Code Generation**:
   - Use AI tools with full context (intent, decisions, patterns, existing code)
   - Provide context to AI including patterns from knowledge/
   - Generate code based on intent
   - Follow established patterns, avoid known anti-patterns
   - Link code to context

2. **Human Supervision**:
   - Review AI-generated code
   - Validate against intent
   - Approve implementation decisions
   - Ensure code quality

3. **Document Decisions**:
   ```markdown
   # Decision: [Title]
   
   ## Context
   [What was the situation?]
   
   ## Decision
   [What did we decide?]
   
   ## Rationale
   [Why did we decide this?]
   
   ## Alternatives
   - [Alternative 1]
   - [Alternative 2]
   ```

4. **Update Context**:
   - Add implementation details to context
   - Link code to intent and decisions
   - Document code-context relationships
   - Keep context up-to-date

**Checklist** (Definition of Done):
- [ ] Code implemented using context
- [ ] Important decisions documented (with rationale)
- [ ] Code linked to context (intent, decisions)
- [ ] Human review completed
- [ ] Context updated with implementation details
- [ ] Code validated against intent

**Tips**:
- Always provide full context to AI
- Document decisions as you make them
- Review AI-generated code carefully
- Keep context updated continuously

---

### Step 3: Learn

**Objective**: Update living context to reflect code changes.

**Activities**:

1. **Update Context** (Primary):
   - Review what changed in your code
   - Use AI to help identify what needs documentation updates
   - Update context to match current codebase state
   - Update decision records if implementation changed
   - Update changelog with significant changes

2. **Preserve Knowledge** (Important):
   - Preserve patterns identified during Build
   - Update patterns based on learnings
   - Document new anti-patterns discovered
   - Store in `context/knowledge/`

3. **Document Learnings** (Optional):
   ```markdown
   # Learning: [Title]
   
   ## Insight
   [What did we learn?]
   
   ## Impact
   [What is the impact?]
   
   ## Action
   [What should we do?]
   ```
   - Note what worked well
   - Document challenges or discoveries

4. **Refine Intent** (If needed):
   - Adjust intent based on learnings
   - Create new work items if needed

**Checklist** (Definition of Done):
- [ ] Context updated to reflect code changes
- [ ] Context aligned with current codebase
- [ ] Changelog updated with significant changes
- [ ] Patterns preserved/updated in knowledge/ (if applicable)
- [ ] Decision records updated if outcomes differ (optional)
- [ ] Learnings documented (optional)
- [ ] Intent refined if needed (optional)

**Tips**:
- Update context as you make code changes
- Use AI to help identify what needs updating
- Keep context simple and current

---

## Integration with Existing Workflows

### With Scrum

- **Sprint Planning**: Use Step 1 (Intent) for each item
- **During Sprint**: Use Step 2 (Build)
- **Sprint Review**: Use Step 3 (Learn)
- **Retrospective**: Refine context and intent

### With Kanban

- **Backlog**: Use Step 1 (Intent) for items
- **In Progress**: Use Step 2 (Build)
- **Done**: Use Step 3 (Learn)

### With DevOps

- **Plan**: Step 1 (Intent)
- **Code/Build**: Step 2 (Build)
- **Deploy/Operate/Monitor**: Step 3 (Learn)

## Common Patterns

### Pattern 1: New Feature Development

1. **Intent**: Define feature intent
2. **Build**: Implement feature with AI, document decisions
3. **Learn**: Deploy and learn from usage

### Pattern 2: Bug Fix

1. **Intent**: Understand bug and fix intent
2. **Build**: Fix bug, document decision
3. **Learn**: Deploy and verify fix

### Pattern 3: Refactoring

1. **Intent**: Define refactoring intent
2. **Build**: Refactor code, document decisions
3. **Learn**: Deploy and monitor

## Tips for Success

1. **Start Small**: Begin with one step, expand gradually
2. **Keep Context Simple**: Don't overcomplicate context structure
3. **Update Continuously**: Keep context up-to-date as you work
4. **Link Everything**: Link code, decisions, and learnings to intent
5. **Learn Regularly**: Extract learnings frequently
6. **Iterate**: Refine your Context Mesh implementation over time

## Context Management Best Practices

### Keep It Simple
- Use simple markdown files
- Don't overcomplicate structure
- Focus on what matters
- **Use Git for versioning** - Don't create files for every small change

### File Creation vs Updates

**Create new file**: Only for new scopes (new feature, new bug, new decision)
**Update existing file**: For refinements, outcomes, evolution (Git versions it)

**Rule**: If it's the same scope, update the file. Git preserves history.

### Update Continuously
- Update context during Build
- Update context during Learn
- Don't let context get stale

### Link Everything
- Link code to intent
- Link decisions to intent
- Link learnings to intent
- Link patterns to decisions and learnings
- Create traceability: Intent → Decision → Learning → Pattern

### Version Control
- Use Git for context versioning
- Commit context updates regularly
- Track context evolution

## Next Steps

- Read [INTEGRATION.md](INTEGRATION.md) for detailed integration guides
- Check [TOOLS.md](TOOLS.md) for tooling recommendations
- See [EXAMPLES.md](EXAMPLES.md) for real-world examples
- Review [FAQ.md](FAQ.md) for common questions

## Getting Help

- Review [FRAMEWORK.md](FRAMEWORK.md) for framework details
- Check [GLOSSARY.md](GLOSSARY.md) for terminology
- See [EXAMPLES.md](EXAMPLES.md) for examples
- Ask questions in [GitHub Discussions](https://github.com)
