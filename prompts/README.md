# Context Mesh Prompts

Ready-to-use prompts. Copy, paste in your AI assistant, answer questions, done.

---

## How to Use

1. **Copy** the prompt from inside the ` ``` ` block
2. **Paste** in your AI assistant (Cursor, Copilot, Claude, etc.)
3. **Answer** the questions
4. **Review** the generated files

That's it.

---

## Setup Prompts

Use these to set up Context Mesh:

| Scenario | Prompt |
|----------|--------|
| **New project** | [new-project.md](new-project.md) |
| **Existing project** | [existing-project.md](existing-project.md) |
| **Client/Freelance** | [freelance-project.md](freelance-project.md) |

## Daily Work Prompts

Use these as you build:

| Scenario | Prompt |
|----------|--------|
| **Add feature** | [add-feature.md](add-feature.md) |
| **Update feature** | [update-feature.md](update-feature.md) |
| **Fix bug** | [fix-bug.md](fix-bug.md) |
| **After implementation** | [learn-update.md](learn-update.md) (manual) |
| **Create agent** | [create-agent.md](create-agent.md) |

**Note:** If you have AGENTS.md configured, AI updates context automatically after implementation.

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
  → AI updates automatically (if AGENTS.md exists)
  → Or use learn-update.md manually
```

---

## The Context Mesh Cycle

```
┌─────────────────────────────────────────────────┐
│                                                 │
│   INTENT              BUILD           LEARN     │
│   ──────              ─────           ─────     │
│   new-project.md      Reference       Auto      │
│   existing-project    @context/       update    │
│   add-feature.md      in prompts      (AGENTS)  │
│   update-feature.md                   or manual │
│   fix-bug.md                          learn-    │
│                                       update.md │
└─────────────────────────────────────────────────┘
```

---

## What Each Prompt Creates

| Prompt | Creates |
|--------|---------|
| new-project.md | Full `context/` structure + AGENTS.md |
| existing-project.md | Full `context/` from codebase analysis + AGENTS.md |
| freelance-project.md | Full `context/` with client requirements + AGENTS.md |
| add-feature.md | feature-*.md + decision (ADR) |
| update-feature.md | Updated feature-*.md + decision if needed |
| fix-bug.md | bug-*.md + decision if needed |
| learn-update.md | Updated status, outcomes, learnings |
| create-agent.md | agent-*.md |

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
- **More details?** See [FRAMEWORK.md](../FRAMEWORK.md)
