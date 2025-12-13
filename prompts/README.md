# Context Mesh Prompts

Ready-to-use prompts to set up and use Context Mesh. Just copy, paste in your AI assistant, and answer questions.

---

## How to Use

1. **Choose** the prompt for your scenario (see table below)
2. **Copy** the prompt from inside the ` ``` ` block
3. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
4. **Answer** the questions
5. **Review** the generated files
6. **Execute** - Use the "Execute" section in each prompt to build/test

**That's it.** No need to create files manually. Each prompt includes:
- Setup instructions
- Templates embedded in the prompt
- Execution section to build/test
- AGENTS.md creation/update instructions

---

## All Prompts

### Setup Prompts

Use these to set up Context Mesh in your project:

| Scenario | Prompt | Description |
|----------|--------|-------------|
| **New project** | [new-project.md](new-project.md) | Starting a project from scratch |
| **Existing project** | [existing-project.md](existing-project.md) | Adding Context Mesh to existing code |
| **Freelance/client** | [freelance-project.md](freelance-project.md) | Client project with requirements |

### Daily Work Prompts

Use these as you build:

| Scenario | Prompt | Description |
|----------|--------|-------------|
| **Add feature** | [add-feature.md](add-feature.md) | Adding new functionality |
| **Update feature** | [update-feature.md](update-feature.md) | Changing existing feature |
| **Fix bug** | [fix-bug.md](fix-bug.md) | Documenting and fixing a bug |
| **After implementation** (optional) | [learn-update.md](learn-update.md) | Manual context update (AI does this automatically if AGENTS.md exists) |
| **Create agent** | [create-agent.md](create-agent.md) | Creating reusable execution pattern |

---

## Quick Reference

```
Starting a project?
  → new-project.md or existing-project.md

Adding something new?
  → add-feature.md

Changing something?
  → update-feature.md

Fixing a bug?
  → fix-bug.md

Done implementing?
  → AI updates context automatically (if AGENTS.md exists)
  → Or use learn-update.md manually

Need a reusable pattern?
  → create-agent.md
```

---

## The Context Mesh Cycle

```
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│   1. INTENT                    2. BUILD                      │
│   ─────────                    ─────────                     │
│   new-project.md               (Your AI assistant)           │
│   existing-project.md          Reference context files       │
│   add-feature.md               in your prompts               │
│   update-feature.md                                          │
│   fix-bug.md                                                 │
│                                                              │
│                       3. LEARN                               │
│                       ────────                               │
│                       AI updates context automatically       │
│                       (AGENTS.md guides this)                │
│                       Or use learn-update.md manually        │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## What Each Prompt Creates

| Prompt | Creates |
|--------|---------|
| new-project.md | Full `context/` structure, project-intent.md, feature intents, changelog, **AGENTS.md** |
| existing-project.md | Full `context/` structure based on codebase analysis, **AGENTS.md** |
| freelance-project.md | Full `context/` structure with client requirements, **AGENTS.md** |
| add-feature.md | feature-*.md + decision (ADR) + updates AGENTS.md |
| update-feature.md | Updated feature-*.md + new decision if needed + updates AGENTS.md |
| fix-bug.md | bug-*.md + decision if needed + updates AGENTS.md |
| learn-update.md | Updated status, outcomes, learnings, changelog |
| create-agent.md | agent-*.md in context/agents/ |

---

## Tips

- **Prompts are self-contained** - All templates are inside the prompt
- **Answer specifically** - More detail = better context
- **Review generated files** - Verify they match your intent
- **Keep context updated** - AI updates automatically if AGENTS.md exists, or use learn-update.md manually

---

## Works With

- ✅ Cursor
- ✅ GitHub Copilot Chat
- ✅ Claude
- ✅ ChatGPT
- ✅ Any AI coding assistant

---

## Need Help?

- **Not sure which prompt?** Start with `new-project.md` or `existing-project.md`
- **Questions?** See [FAQ.md](../FAQ.md)
- **More details?** See [GETTING_STARTED.md](../GETTING_STARTED.md)
