<div align="center">

<a href="context-mesh.org">
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

Context Mesh is a simple 3-step framework that makes AI generate consistent, maintainable code by preserving context.

```
❌ Without Context Mesh:
   "Create a login component"
   → AI generates generic code, no patterns, hard to maintain

✅ With Context Mesh:
   "Implement login following @context/intent/feature-user-auth.md"
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

---

## Quick Start (2 minutes)

### Option 1: New Project

```bash
# Copy this prompt to your AI assistant (Cursor, Copilot, Claude)
```

👉 **[prompts/new-project.md](prompts/new-project.md)** - AI creates the entire Context Mesh structure

### Option 2: Existing Project

```bash
# AI analyzes your codebase and creates context
```

👉 **[prompts/existing-project.md](prompts/existing-project.md)** - Add Context Mesh to existing code

### After Setup

Use these prompts as you work:

| I want to... | Use this |
|--------------|----------|
| Add a feature | [add-feature.md](prompts/add-feature.md) |
| Fix a bug | [fix-bug.md](prompts/fix-bug.md) |
| Update a feature | [update-feature.md](prompts/update-feature.md) |

---

## Real Results

> **10 days** to migrate a complex monolith to micro-frontends (2 developers)
> 
> *This typically takes months.*

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
