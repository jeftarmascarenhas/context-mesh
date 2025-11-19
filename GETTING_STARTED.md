# Getting Started with LCF

This guide will help you get started with the Living Context Framework (LCF) in your project.

## Prerequisites

Before starting with LCF, ensure you have:

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
mkdir -p context/{intent,decisions,learnings}
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

## Hypotheses
- [Hypothesis 1]
- [Hypothesis 2]
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
│   │   └── initial-intent.md
│   ├── decisions/
│   │   └── (decision records)
│   └── learnings/
│       └── (learning insights)
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

1. **Define Intent**:
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

2. **Document Hypotheses**:
   ```markdown
   # Hypotheses
   
   ## Hypothesis 1: [Title]
   - **If** we [action]
   - **Then** [expected outcome]
   - **Because** [reasoning]
   ```

3. **Create Initial Context**:
   - Store intent in your context repository
   - Link to project structure
   - Make it accessible to AI tools

**Checklist**:
- [ ] Intent statement clear and validated
- [ ] Hypotheses documented
- [ ] Initial context created
- [ ] Stakeholders aligned

**Tips**:
- Keep intent simple and focused
- Make intent measurable
- Align with stakeholders early

---

### Step 2: Build

**Objective**: AI builds with context, human supervises, and decisions are documented.

**Activities**:

1. **AI Code Generation**:
   - Use AI tools with full context
   - Provide context to AI (intent, decisions, existing code)
   - Generate code based on intent
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

**Checklist**:
- [ ] Code implemented using context
- [ ] Important decisions documented
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

**Objective**: Learn from results and update living context.

**Activities**:

1. **Observe Results**:
   - Monitor metrics and logs
   - Collect user feedback
   - Track system behavior
   - Link observability to context

2. **Extract Learnings**:
   ```markdown
   # Learning: [Title]
   
   ## Insight
   [What did we learn?]
   
   ## Impact
   [What is the impact?]
   
   ## Action
   [What should we do?]
   
   ## Context Updates
   - [Update 1]
   - [Update 2]
   ```

3. **Update Context**:
   - Add learnings to context
   - Update decision records with outcomes
   - Refine intent if needed
   - Create new hypotheses

4. **Feedback Loop**:
   - Feed insights back to Intent step
   - Refine intent based on outcomes
   - Create new work items from learnings
   - Improve processes

**Checklist**:
- [ ] Results observed and analyzed
- [ ] Learnings extracted and validated
- [ ] Living context updated with learnings
- [ ] Intent refined if needed
- [ ] Feedback loop to Intent initiated

**Tips**:
- Observe results continuously
- Extract learnings regularly
- Update context immediately
- Use learnings to improve

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
6. **Iterate**: Refine your LCF implementation over time

## Context Management Best Practices

### Keep It Simple
- Use simple markdown files
- Don't overcomplicate structure
- Focus on what matters

### Update Continuously
- Update context during Build
- Update context during Learn
- Don't let context get stale

### Link Everything
- Link code to intent
- Link decisions to intent
- Link learnings to intent
- Create traceability

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
