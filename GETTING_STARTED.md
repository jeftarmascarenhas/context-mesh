# Getting Started with Context Mesh

This guide will help you get started with Context Mesh in your project.

## Prerequisites

Before starting with Context Mesh, ensure you have:

- A development project (new or existing)
- Git repository (recommended)
- AI development tools (Cursor, GitHub Copilot, etc.)
- Team familiar with Agile/Scrum concepts (helpful but not required)

## Quick Start (Choose Your Path)

Context Mesh can be initialized in two ways. Choose the approach that works best for you:

### Option A: AI-Assisted Init (Recommended - 2 minutes) ⚡

**Fastest way to get started** - Use AI to create the complete Context Mesh structure automatically.

#### Step 1: Use a Prompt Template

Copy and adapt a prompt from [prompts/](prompts/) based on your scenario:

- **New Project**: Use [prompts/new-project.md](prompts/new-project.md)
- **Existing Project**: Use [prompts/existing-project.md](prompts/existing-project.md)
- **Freelance Project**: Use [prompts/freelance-project.md](prompts/freelance-project.md)

See [prompts/README.md](prompts/README.md) for a complete guide to all available prompts.

**Example for New Project:**
```
Create a Context Mesh structure for a [PROJECT_TYPE] project following 
the Context Mesh framework.

Project details:
- Name: [YOUR_PROJECT_NAME]
- Type: [web app / API / mobile app / etc]
- Tech Stack: [if known]
- Main Features: [list features]

Create:
1. The complete context/ directory structure
2. Initial project-intent.md with What, Why, and Success Criteria
3. A basic AGENTS.md file referencing the context files
4. Initial changelog.md

Follow the structure from @examples/todo-app-complete/context/ as reference.
```

#### Step 2: Review and Refine

1. Review the generated files
2. Refine `project-intent.md` with your specific details
3. Add any additional decisions or patterns as needed

⏱️ **Total Time**: ~2 minutes

**✅ Done!** You're ready to start using Context Mesh. Continue to [Step-by-Step Implementation](#step-by-step-implementation) below.

---

### Option B: Manual Setup (5 minutes) 📝

**Prefer to create files manually?** Follow these steps:

#### 📋 Quick Start Checklist

```
🚀 Getting Started
├── ☐ Read FRAMEWORK.md (understand 3-step workflow)
├── ☐ Create context/ directory structure
├── ☐ Create your first project-intent.md
└── ☐ Ready to start Intent phase!
```

**Progress**: [ ] 0/4 completed

#### Step 1: Understand the Framework

Read the [FRAMEWORK.md](FRAMEWORK.md) to understand the 3-step workflow.

⏱️ **Time**: ~15 minutes

#### Step 2: Initialize Context

Create a `context/` directory in your project:

```bash
mkdir -p context/{intent,decisions,knowledge/{patterns,anti-patterns},evolution}
```

⏱️ **Time**: ~30 seconds

#### Step 3: Start with Intent

Create your first intent document:

```bash
cat > context/intent/project-intent.md << 'EOF'
# Project Intent

## What
[Describe what you want to build]

## Why
[Why is this important?]

## Success Criteria
- [Criterion 1]
- [Criterion 2]

## Status
- **Created**: YYYY-MM-DD (Phase: Intent)
- **Status**: Draft
EOF
```

⏱️ **Time**: ~5 minutes

#### Step 4: Follow the Workflow

Proceed through the 3 steps:
1. ✅ **Intent** (you just did this)
2. ⏳ **Build** (next step)
3. ⏳ **Learn** (after build)

**Next**: Continue to [Step-by-Step Implementation](#step-by-step-implementation) below for detailed guidance.

## Detailed Setup

### 1. Project Structure

Create the following directory structure:

```
your-project/
├── AGENTS.md          # Optional: Router for AI agents (references Context Mesh)
├── context/           # Context Mesh: strategic context
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

**Note**: `AGENTS.md` is optional but recommended. It acts as a router that references Context Mesh files, providing operational instructions (setup, commands, conventions) while Context Mesh provides strategic context (intent, decisions, knowledge). See [TOOLS.md](TOOLS.md) for details.

### 2. Context Management

You can use simple markdown files or any documentation system. The key is to:
- Keep context simple and focused
- Update context continuously
- Link everything to intent
- Version control your context (using Git)

## Step-by-Step Implementation

### 📍 Your Progress

```
Context Mesh Workflow
├── ✅ Setup Complete
├── ⏳ Step 1: Intent (Current)
├── ⬜ Step 2: Build
└── ⬜ Step 3: Learn
```

---

### Step 1: Intent

**Objective**: Plan and prepare context before building. This is the **planning phase** where you define what to build, create feature intents, make technical decisions, and prepare everything needed for efficient Build phase.

**Activities**:

1. **Define Intent** (can be initial or refined):
   - Create `project-intent.md` for overall project scope
   - Create `feature-*.md` for each new feature
   - Create `bug-*.md` for each bug fix
   - Create `refactor-*.md` for refactoring work
   ```markdown
   # Intent Statement
   
   ## What
   [What do you want to build?]
   
   ## Why
   [Why is this important?]
   
   ## Success Criteria
   - [Criterion 1]
   - [Criterion 2]
   
   ## Status
   
   - **Created**: YYYY-MM-DD (Phase: Intent)
   - **Status**: Draft
   ```

2. **Create Technical Decisions** (recommended in Step 1):
   - Plan technical decisions when you know the approach
   - Create `decisions/*.md` files before Build
   - Makes Build phase faster (AI has decisions ready)
   - See [FRAMEWORK.md](FRAMEWORK.md) for decision format

3. **Identify or Define Patterns** (for existing/new projects):
   - **Existing projects**: Identify existing patterns in codebase
   - **New projects**: Define initial patterns based on team experience
   - Store in `context/knowledge/patterns/`

4. **Create Initial Context**:
   - Store intent in your context repository
   - Link to project structure
   - Make it accessible to AI tools

**Checklist** (Definition of Done):

```
✅ Intent Phase Checklist
├── ☐ Intent statement clear and validated (What + Why)
├── ☐ Feature/Bug/Refactor intent created (if applicable)
├── ☐ Technical decisions created (if known) - ⭐ Recommended (makes Build faster)
├── ☐ Initial patterns identified (existing) or defined (new)
├── ☐ Initial context created and stored
└── ☐ Stakeholders aligned on intent
```

**Progress**: [ ] 0/6 completed

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
   - **Use simple prompts that reference context files** (context is primary, prompts should be minimal)
   - Generate code based on intent
   - Follow established patterns, avoid known anti-patterns
   - Link code to context

   **Approach Hierarchy:**
   
   **1. Simple Prompts (Recommended - Start Here):**
   ```
   Implement authentication following @context/intent/feature-user-auth.md
   and @context/decisions/002-auth-approach.md
   ```
   The context files contain all details - the prompt just directs the AI to the right context.
   
   **2. AI Agents (Advanced - When Needed):**
   For complex projects or teams, use `agents/agent-*.md` files for structured execution.
   See [ADVANCED.md](ADVANCED.md) for details.
   
   **3. Detailed Prompts (Avoid):**
   Avoid writing long prompts that repeat context. If needed frequently, create an agent file instead.
   
   **Start simple, add complexity only when needed.**

2. **Human Supervision**:
   - Review AI-generated code
   - Validate against intent
   - Approve implementation decisions
   - Ensure code quality

3. **Create or Update Decisions**:
   - Use decisions from Step 1 if they exist (recommended approach)
   - Create new decisions if technical choices emerge during Build
   - Update existing decisions if implementation approach differs from plan
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
   
   ## Outcomes
   (Updated in Step 3: Learn after implementation)
   ```

4. **Update Context**:
   - Add implementation details to context
   - Link code to intent and decisions
   - Document code-context relationships
   - Keep context up-to-date

**Checklist** (Definition of Done):

```
✅ Build Phase Checklist
├── ☐ Code implemented using context
├── ☐ Important decisions documented (with rationale)
├── ☐ Code linked to context (intent, decisions)
├── ☐ Human review completed
├── ☐ Context updated with implementation details
└── ☐ Code validated against intent
```

**Progress**: [ ] 0/6 completed

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
   - Update decision records with outcomes (what actually happened)
   - Create new improvement decisions if learnings suggest better approaches
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

```
✅ Learn Phase Checklist
├── ☐ Context updated to reflect code changes (Required)
├── ☐ Context aligned with current codebase (Required)
├── ☐ Changelog updated with significant changes (Required)
├── ☐ Patterns preserved/updated in knowledge/ (If applicable)
├── ☐ Decision records updated with outcomes (Optional)
├── ☐ New improvement decisions created if needed (Optional)
├── ☐ Learnings documented (Optional)
└── ☐ Intent refined if needed (Optional)
```

**Progress**: [ ] 0/8 completed (3 required, 5 optional)

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

### Status and Dates

Every context file should include a **Status** section to track lifecycle and provide traceability.

**Why it matters**:
- Know when something was created or updated
- Track the evolution of context over time
- Understand the current state of each artifact
- Help AI agents understand relevance and current state

**Format**:
```markdown
## Status

- **Created**: YYYY-MM-DD (Phase: Intent/Build/Learn)
- **Status**: [Status Type]
- **Updated**: YYYY-MM-DD (Phase: Intent/Build/Learn) - [reason] (optional)
```

**Status Types**:
- **Intent Files** (feature-*.md, bug-*.md): Draft, In Progress, Completed, Deprecated, Resolved
- **Decision Files** (decisions/*.md): Proposed, Accepted, Superseded, Deprecated
- **Knowledge Files** (patterns/*.md): Active, Deprecated, Superseded
- **Learning Files** (learning-*.md): Active, Archived

**When to Update**:
- **Created**: Always include when file is first created
- **Status**: Update when status changes (e.g., Draft → In Progress → Completed)
- **Updated**: Add when you make significant updates (not every small change)

See [FRAMEWORK.md](FRAMEWORK.md) for complete details on Status and Dates.

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

- **Quick Init**: See [prompts/](prompts/) for AI-assisted initialization templates
- Read [INTEGRATION.md](INTEGRATION.md) for detailed integration guides
- Check [TOOLS.md](TOOLS.md) for tooling recommendations
- See [EXAMPLES.md](EXAMPLES.md) for real-world examples
- Review [FAQ.md](FAQ.md) for common questions

## Getting Help

- Review [FRAMEWORK.md](FRAMEWORK.md) for framework details
- Check [GLOSSARY.md](GLOSSARY.md) for terminology
- See [EXAMPLES.md](EXAMPLES.md) for examples
- Ask questions in [GitHub Discussions](https://github.com)
