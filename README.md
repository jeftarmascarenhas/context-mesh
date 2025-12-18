<div align="center">

<a href="https://context-mesh.org">
<img src="./images/context-mesh-icon-medium.png" height="200" alt="Context Mesh" aria-label="context-mesh.org">
</a>

# Context Mesh

### Stop blaming the AI model. The problem is missing context.

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/jeftarmascarenhas/context-mesh/releases)
[![Framework](https://img.shields.io/badge/framework-AI--First-purple.svg)](https://github.com/jeftarmascarenhas/context-mesh)
[![Status](https://img.shields.io/badge/status-active-success.svg)](https://github.com/jeftarmascarenhas/context-mesh)

</div>

---

## The Real Problem

You prompt. AI generates. Code works... sometimes.

Three months later, you open that codebase: *"Why did we do this? What was the reasoning?"* 

The context is gone. The decisions are forgotten. **You spend hours reconstructing what you already knew.**

This isn't an AI model problem. **It's a context problem.**

---

## The Solution: Context Mesh

Context Mesh is a simple 3-step framework that **standardizes AI-assisted development** by planning first and preserving context in your repo.

```
❌ Without Context Mesh:
   "Create a login component"
   → AI generates generic code, no patterns, hard to maintain

✅ With Context Mesh:
   "Implement login following @context/intent/feature-user-auth.md"
   → You planned first (intent + decision) before writing code
   → Feature defines WHAT and WHY
   → Feature references decision with HOW (tech approach)
   → AI generates code following YOUR patterns, YOUR decisions
```

**Result:** Even free models deliver quality code when they have structured context.

**How it connects:**
```
feature-user-auth.md          →  "What: User authentication"
    ↓                             "Why: Secure access needed"
    └── References:               "See: decisions/002-auth.md"
            ↓
        002-auth.md           →  "Decision: Use JWT"
                                  "Rationale: Stateless, scalable"
```

One simple prompt loads all the context AI needs.

> **Tool-agnostic note:** In Cursor you can reference files with `@path`. In other AI tools, attach or paste the referenced files (intent/decisions) so the model can read them.

---

## How It Works (3 Steps)

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   INTENT    │ ──► │    BUILD    │ ──► │    LEARN    │
│  What & Why │     │  AI + Human │     │   Update    │
└─────────────┘     └─────────────┘     └─────────────┘
                                               │
                          ◄────────────────────┘
                              Feedback Loop
```

1. **Intent** - Define what to build and why (create context)
2. **Build** - AI generates code, human supervises
3. **Learn** - Update context with outcomes

That's it. Each step preserves context for the next.

### What Each Step Produces (In Practice)

#### 1) Intent (Plan First)

You write down **WHAT** you're building, **WHY** it matters, and **how you know it's done** (acceptance criteria). If the feature needs a non-trivial approach, you also capture the **Decision (ADR)** before writing code.

This is the **minimum viable Context Mesh**: intent + decision (so AI stops guessing).

```
context/
├── intent/
│   ├── project-intent.md           # high-level goals + constraints
│   └── feature-user-auth.md        # what/why + acceptance criteria
└── decisions/
    └── 002-auth.md                 # how (approach) + rationale (ADR)
```

**Optional (recommended) full structure:** Add more context as your project grows.

```
your-project/
├── context/
│   ├── intent/                     # what + why (requirements)
│   │   ├── project-intent.md
│   │   ├── feature-*.md
│   │   └── bug-*.md
│   ├── decisions/                  # how (ADRs)
│   │   └── 001-*.md
│   ├── knowledge/                  # standards that make AI consistent
│   │   ├── patterns/
│   │   └── anti-patterns/
│   ├── agents/                     # optional: reusable execution playbooks
│   │   └── agent-*.md
│   └── evolution/                  # what changed over time
│       └── changelog.md
└── AGENTS.md                       # agent router (optional but recommended)
```

#### 2) Build (AI + Human)

You implement by referencing the intent (and any relevant decisions/patterns). AI generates code that matches your standards; you review and ship.

#### 3) Learn (Keep Context Alive)

After shipping, you update context with what actually happened (outcomes, gotchas, changes to approach). This prevents context drift over time.

### Use the Steps, Adapt the Structure

Keep the **3 steps** (Intent → Build → Learn), but feel free to adapt the structure to your reality:
- Rename folders/files, add fields, integrate with Scrum/Kanban, etc.
- The goal is consistent AI output via **versioned context**, not rigid file layouts.

---

## Quick Start (2 minutes)

### Option 1: New Project

1. Open **[prompts/new-project.md](prompts/new-project.md)**
2. **Copy** the prompt (inside the ``` block)
3. **Paste** into your AI assistant (Cursor, Copilot, Claude, etc.)
4. **Answer** the questions
5. **Review** generated files (`context/` + `AGENTS.md`)

### Option 2: Existing Project

1. Open **[prompts/existing-project.md](prompts/existing-project.md)**
2. **Copy** the prompt (inside the ``` block)
3. **Paste** into your AI assistant
4. Let it **analyze your codebase** and generate living context
5. **Review** generated files (`context/` + `AGENTS.md`)

### After Setup

Use these prompts as you work:

| I want to... | Use this |
|--------------|----------|
| Add a feature | [add-feature.md](prompts/add-feature.md) |
| Fix a bug | [fix-bug.md](prompts/fix-bug.md) |
| Update a feature | [update-feature.md](prompts/update-feature.md) |
| Update context (Learn step) | [learn-update.md](prompts/learn-update.md) |

---

## Real Results

> **15 days** to migrate the **front-end** of a React monolith into **10 micro front-ends** (2 developers, real production work)
>
> Breakdown: **4–5 days in Intent (planning)** + remaining days in **Build + Learn** (continuous context updates during Build/Learn)

The monolith was an **AI automation platform** with **10 internal tools**. The code was hard to understand and had **no consistent standards**.

**What changed in the Build step:**
- Migrated each tool to a **newer React** baseline
- Switched UI from **Material UI → shadcn/ui**
- Introduced **React Query** (previously not used)
- Adopted `@module-federation/vite` for micro front-end composition

**Another example:**
- Built [`context-mesh.org`](https://context-mesh.org) with **2–3 hours** in Intent planning and **< 1 hour** in Build, then Learn to keep context current

**What teams report:**
- ✅ Faster development cycles
- ✅ New developers onboard in days, not weeks
- ✅ Code remains understandable months later
- ✅ AI generates consistent code that follows your patterns

[See more examples →](EXAMPLES.md)

---

## What Gets Created

```
your-project/
├── context/
│   ├── intent/           # What and why
│   │   ├── project-intent.md
│   │   └── feature-*.md
│   ├── decisions/        # Technical decisions (ADR)
│   │   └── 001-*.md
│   ├── knowledge/        # Patterns to follow
│   │   ├── patterns/
│   │   └── anti-patterns/
│   └── evolution/        # Changes and learnings
│       └── changelog.md
└── AGENTS.md             # AI agent router
```

**That's all.** Simple markdown files. Version controlled with Git.

---

## Why It Works

Traditional:
```
Code → Documentation (often incomplete)
```

Context Mesh:
```
Context → Code (always complete)
```

When context is primary:
- AI understands your architecture
- Decisions preserve their "why"
- Code follows your patterns
- Knowledge evolves with your system
- You repeat less in prompts (less re-explaining), and the AI infers less

---

## Learn More

| I want to... | Read this |
|--------------|-----------|
| Start now | [prompts/](prompts/) ⚡ |
| Understand the framework | [FRAMEWORK.md](FRAMEWORK.md) |
| See examples | [examples/](examples/) |
| Use with Scrum/Agile | [INTEGRATION.md](INTEGRATION.md) |
| Common questions | [FAQ.md](FAQ.md) |

---

## Works With

- ✅ Cursor
- ✅ GitHub Copilot
- ✅ Claude
- ✅ ChatGPT
- ✅ Any AI coding assistant

---

## Contributing

Context Mesh is in active development. Contributions, feedback, and use cases are welcome!

- **Issues**: [GitHub Issues](https://github.com/jeftarmascarenhas/context-mesh/issues)
- **Discussions**: [GitHub Discussions](https://github.com/jeftarmascarenhas/context-mesh/discussions)

## License

[MIT License](LICENSE)

---

<div align="center">

**Ready to fix the context crisis?**

**[Get Started →](prompts/)** • **[See Examples →](examples/)** • **[Read Framework →](FRAMEWORK.md)**

Made with ❤️ for the AI-First development community

</div>
