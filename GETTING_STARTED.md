# Getting Started with Context Mesh

This guide shows you how to use Context Mesh in practice. For concepts, see [README.md](README.md).

---

## Quick Start (30 seconds)

**Choose your scenario:**

| I'm... | Use this prompt |
|--------|----------------|
| Starting a new project | [new-project.md](prompts/new-project.md) |
| Adding Context Mesh to existing code | [existing-project.md](prompts/existing-project.md) |
| Working on a client/freelance project | [freelance-project.md](prompts/freelance-project.md) |

**What happens:**
1. Copy the prompt → Paste in your AI assistant → Answer questions
2. AI creates `context/` folder structure + `AGENTS.md`
3. You're ready to build features with context

---

## The Context Mesh Mindset (1 min read)

### Plan First, Then Build

Context Mesh flips traditional development:

```
❌ Traditional: Code → Documentation (often incomplete)
✅ Context Mesh: Context → Code (always complete)
```

**The 3-step flow:**
1. **Intent** - Define WHAT and WHY (plan first)
2. **Build** - AI generates code following your context
3. **Learn** - Update context with outcomes

### Minimum Viable Context

Start simple. You only need **intent + decision** to get started:

```
context/
├── intent/
│   └── feature-user-auth.md        # What + Why + Acceptance criteria
└── decisions/
    └── 002-auth.md                 # How (technical approach) + Rationale
```

This is enough. AI stops guessing because it has:
- **What** you're building (feature intent)
- **Why** it matters (business reason)
- **How** to build it (technical decision)

**Optional (add as you grow):** patterns, anti-patterns, agents, knowledge base.

### Tool-Agnostic Note

The `@context/` syntax works in Cursor. For other AI tools (GitHub Copilot, Claude, ChatGPT):
- Use the full file path: `context/intent/feature-user-auth.md`
- Or copy the file content and paste it into your AI chat

---

## Your First Feature (5 min walkthrough)

Let's add user authentication. This shows the complete flow:

### Step 1: Intent (Plan First)

**Action:** Open [prompts/add-feature.md](prompts/add-feature.md), copy the prompt, paste in your AI assistant.

**You answer:**
- Feature name: `user-auth`
- What it does: Users can sign up, login, logout
- Why: Secure access to the application
- Acceptance criteria: User can signup, login, logout successfully
- Technical approach: JWT tokens with httpOnly cookies

**AI creates:**
```
context/
├── intent/
│   └── feature-user-auth.md        # What + Why + Acceptance criteria
└── decisions/
    └── 002-jwt-authentication.md    # How (JWT) + Rationale (stateless, scalable)
```

**Why this matters:** You planned the approach BEFORE writing code. AI won't guess.

### Step 2: Build (AI + Human)

**Action:** In your AI assistant, type:

```
Implement user authentication following @context/intent/feature-user-auth.md
```

**What AI sees:**
- Feature intent (what + why + acceptance criteria)
- Decision (JWT approach + rationale)
- Existing patterns in `context/knowledge/patterns/` (if any)

**What you do:**
- Review generated code
- Test it works
- Approve changes

**Result:** Code that follows YOUR decisions, YOUR patterns.

### Step 3: Learn (Keep Context Alive)

**Action:** After implementation, update context with outcomes.

**If you have `AGENTS.md`:** AI updates automatically.

**If not:** Use [prompts/learn-update.md](prompts/learn-update.md)

**What gets updated:**
- Feature marked as complete
- Decision updated with outcomes (what worked, what didn't)
- Changelog updated

**Why this matters:** Context stays current. Three months later, you know what happened.

---

## Daily Workflow

### The 3-Step Flow (Every Time)

Every feature, bug fix, or update follows the same pattern:

```
Intent → Build → Learn
```

| Step | What You Do | What Gets Created/Updated |
|------|-------------|---------------------------|
| **Intent** | Use a prompt to define what/why | `context/intent/feature-*.md` + `context/decisions/*.md` |
| **Build** | Reference intent in AI prompt | Code that follows your context |
| **Learn** | Update context with outcomes | Context stays current |

### Quick Reference: I Want To...

| I want to... | Do this |
|--------------|---------|
| **Add a feature** | Use [add-feature.md](prompts/add-feature.md) → Build → Learn |
| **Fix a bug** | Use [fix-bug.md](prompts/fix-bug.md) → Build → Learn |
| **Update a feature** | Use [update-feature.md](prompts/update-feature.md) → Build → Learn |
| **Update context manually** | Use [learn-update.md](prompts/learn-update.md) |

### When to Use Prompts vs Agents

**Use Prompts (Simple - Default):**
- Most features
- Simple tasks
- One-time work

**Example:**
```
Implement [feature] following @context/intent/feature-[name].md
```

**Use Agents (Advanced - When Needed):**
- Complex features with multiple steps
- Team standardization
- Repeated patterns

**Example:**
```
Execute @context/agents/agent-auth.md for the login feature
```

**Decision guide:** Start with prompts. Add agents when you find yourself writing the same detailed instructions repeatedly.

See [ADVANCED.md](ADVANCED.md) for agent details.

---

## Prompts Reference

### Setup Prompts

| Prompt | When to Use |
|--------|-------------|
| [new-project.md](prompts/new-project.md) | Starting a brand new project |
| [existing-project.md](prompts/existing-project.md) | Adding Context Mesh to existing code |
| [freelance-project.md](prompts/freelance-project.md) | Client or freelance work |

### Daily Work Prompts

| Prompt | When to Use |
|--------|-------------|
| [add-feature.md](prompts/add-feature.md) | Adding a new feature |
| [update-feature.md](prompts/update-feature.md) | Changing an existing feature |
| [fix-bug.md](prompts/fix-bug.md) | Fixing a bug |
| [learn-update.md](prompts/learn-update.md) | Manually updating context after changes |
| [create-agent.md](prompts/create-agent.md) | Creating a reusable execution pattern |

---

## Key Rules

| Rule | Why |
|------|-----|
| **ADR before code** | Decision must exist before implementing (AI stops guessing) |
| **Feature references decision** | Creates traceability (why this approach?) |
| **Update context after changes** | Keeps context current (no drift) |
| **Don't over-document** | Focus on what matters (intent + decisions) |

---

## Next Steps

- **See it in action:** [examples/](examples/) - Full working examples
- **Deep dive:** [FRAMEWORK.md](FRAMEWORK.md) - Complete framework details
- **Questions:** [FAQ.md](FAQ.md) - Common questions
- **Integration:** [INTEGRATION.md](INTEGRATION.md) - Use with Scrum/Kanban

---

**Ready?** Start with [prompts/new-project.md](prompts/new-project.md) or [prompts/existing-project.md](prompts/existing-project.md)
