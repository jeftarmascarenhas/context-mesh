# Getting Started with Context Mesh

This guide shows you how to use Context Mesh in practice. For concepts, see [README.md](README.md).

---

## 1. Setup Your Project

Choose your scenario and copy the prompt to your AI assistant:

| Scenario | Prompt |
|----------|--------|
| New project | [new-project.md](prompts/new-project.md) |
| Existing project | [existing-project.md](prompts/existing-project.md) |
| Client/Freelance | [freelance-project.md](prompts/freelance-project.md) |

**After running the prompt**, you'll have:
```
your-project/
├── context/
│   ├── intent/
│   ├── decisions/
│   ├── knowledge/
│   └── evolution/
└── AGENTS.md
```

---

## 2. Daily Workflow

### Adding a Feature

**Step 1: Create intent and decision**
```
Use prompt: prompts/add-feature.md
```

This creates:
- `context/intent/feature-[name].md` - What and why
- `context/decisions/[number]-[name].md` - Technical approach (ADR)

**Step 2: Build**
```
Implement [feature] following @context/intent/feature-[name].md
```

AI reads your context and generates code following your decisions.

**Step 3: Learn** (automatic if AGENTS.md exists, or use `learn-update.md`)

---

### Fixing a Bug

**Step 1: Document the bug**
```
Use prompt: prompts/fix-bug.md
```

**Step 2: Fix**
```
Fix the bug following @context/intent/bug-[name].md
```

**Step 3: Learn** (marks as resolved, updates changelog)

---

### Updating a Feature

**Step 1: Update intent**
```
Use prompt: prompts/update-feature.md
```

**Step 2: Implement changes**
```
Implement changes following @context/intent/feature-[name].md
```

---

## 3. Example: Complete Flow

Let's add user authentication:

### Intent
```
# Use add-feature.md prompt, answer:
- Feature name: user-auth
- What it does: Users can sign up, login, logout
- Why: Secure access to the application
- Technical approach: JWT tokens
```

**Created files:**
- `context/intent/feature-user-auth.md`
- `context/decisions/002-jwt-authentication.md`

### Build
```
Implement user authentication following @context/intent/feature-user-auth.md
```

AI sees:
- Feature intent (what + why + success criteria)
- Decision (JWT approach + rationale)
- Existing patterns in `context/knowledge/patterns/`

### Learn

AI automatically (or via `learn-update.md`):
- Marks feature as complete
- Adds outcomes to decision
- Updates changelog

---

## 4. Key Rules

| Rule | Why |
|------|-----|
| **ADR before code** | Decision must exist before implementing |
| **Feature references decision** | Creates traceability |
| **Update context after changes** | Keeps context current |
| **Don't over-document** | Focus on what matters |

---

## 5. Prompts Reference

### Setup
| Prompt | Use |
|--------|-----|
| [new-project.md](prompts/new-project.md) | Starting fresh |
| [existing-project.md](prompts/existing-project.md) | Adding to existing code |
| [freelance-project.md](prompts/freelance-project.md) | Client work |

### Daily Work
| Prompt | Use |
|--------|-----|
| [add-feature.md](prompts/add-feature.md) | New feature |
| [update-feature.md](prompts/update-feature.md) | Change feature |
| [fix-bug.md](prompts/fix-bug.md) | Bug fix |
| [learn-update.md](prompts/learn-update.md) | Manual context update |
| [create-agent.md](prompts/create-agent.md) | Reusable execution pattern |

---

## 6. Using Agents (Optional)

Agents are reusable execution patterns for more control:

```
Execute @context/agents/agent-auth.md for the login feature
```

Agent loads all relevant context and follows structured steps.

**When to use agents:**
- Complex features with multiple steps
- Team standardization
- Repeated patterns

See [ADVANCED.md](ADVANCED.md) for details.

---

## Next Steps

- **Deep dive:** [FRAMEWORK.md](FRAMEWORK.md) - Complete framework details
- **Examples:** [examples/](examples/) - Full working examples
- **Questions:** [FAQ.md](FAQ.md) - Common questions
