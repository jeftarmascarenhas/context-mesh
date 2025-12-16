# Prompt: Create Agent

Use this prompt to create a reusable agent (execution pattern) for your Context Mesh project.

## How to Use

1. **Copy the prompt** below
2. **Paste in your AI assistant** (Cursor, Copilot, Claude, etc.)
3. **Answer questions** about the agent
4. **Review** the generated agent file

---

## Prompt

```
I want to create a reusable agent for my Context Mesh project.

Agents are simple markdown files in context/agents/ that define how to execute specific tasks. They reference Context Mesh files (intent, decisions, patterns) and provide step-by-step execution instructions.

Key principle: Agents should REFERENCE context, not duplicate it. All details are in context files - agents just tell AI how to execute.

Please help me create an agent file.

Ask me:
1. What is the agent name? (e.g., "backend-api", "frontend-component", "database-migration")
2. What does this agent do? (one sentence purpose)
3. Which context files does it need? (feature intents, decisions, patterns)
4. What are the execution steps? (step-by-step what to do)
5. What does it produce? (outputs)

After I answer, create:

context/agents/agent-[name].md

Use this template:

---
AGENT-[NAME].MD TEMPLATE:
---
# Agent: [AGENT_NAME]

## Purpose
[One sentence - what this agent does]

## Context Files to Load
- @context/intent/feature-[name].md (if applicable)
- @context/decisions/[number]-[name].md (if applicable)
- @context/knowledge/patterns/[pattern].md (if applicable)

## Execution Steps
1. Load context files listed above
2. [Step 1 - what to do]
3. [Step 2 - what to do]
4. [Step 3 - what to do]
5. [Step 4 - what to do]

## Definition of Done
Technical criteria that must be met before this agent's task is complete:
- [ ] [Criterion 1 - e.g., Code compiles without errors]
- [ ] [Criterion 2 - e.g., Tests pass]
- [ ] [Criterion 3 - e.g., Context updated]

## Output
- [Output 1]
- [Output 2]

## Related
- Feature: [if applicable]
- Decision: [if applicable]
- Pattern: [if applicable]
---

Remember: Keep it simple. Reference context files, don't duplicate their content.
```

---

## What This Prompt Does

- **Creates agent file** - Simple reusable execution pattern
- **References context** - Links to intent, decisions, patterns
- **Defines steps** - Clear execution instructions
- **Keeps it simple** - No duplication of context

---

## When to Create an Agent

Create an agent when:
- ✅ You write the same detailed prompt repeatedly
- ✅ You want to standardize task execution
- ✅ Working with a team (shared patterns)
- ✅ Complex task needs structured steps

**Don't create** if simple prompts work fine.

---

## Example Use Cases

- **Backend API agent** - Standardized API endpoint creation
- **Frontend component agent** - Component creation pattern
- **Database migration agent** - Migration workflow
- **Test creation agent** - Testing pattern
- **Feature-specific agents** - Reusable feature implementation

---

## After Creating the Agent

Use it in your prompts:

```
Execute @context/agents/agent-[name].md for [feature/task]
```

The AI will:
1. Read the agent file
2. Load referenced context files
3. Follow execution steps
4. Produce outputs

---

## Tips

- **Keep it simple** - Agents are just reusable prompts
- **Reference, don't duplicate** - All details in context files
- **Update when context changes** - Keep agents aligned with context
- **Start simple** - You can always add more detail later

