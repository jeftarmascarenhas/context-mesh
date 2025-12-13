# Getting Started with Context Mesh

Context Mesh helps you build with AI while keeping your code maintainable. It's a simple **3-step process**: Intent → Build → Learn.

---

## Quick Start (2 minutes)

### Step 1: Choose Your Scenario

| I want to... | Use this prompt |
|--------------|-----------------|
| Start a new project | [new-project.md](prompts/new-project.md) |
| Add Context Mesh to existing project | [existing-project.md](prompts/existing-project.md) |
| Start a freelance/client project | [freelance-project.md](prompts/freelance-project.md) |

### Step 2: Copy and Paste

1. Open the prompt file
2. Copy the prompt inside the ` ``` ` block
3. Paste in your AI assistant (Cursor, Copilot, Claude, etc.)
4. Answer the questions

### Step 3: Start Building

Your Context Mesh structure is ready. Use these prompts as you work:

| I want to... | Use this prompt |
|--------------|-----------------|
| Add a new feature | [add-feature.md](prompts/add-feature.md) |
| Update an existing feature | [update-feature.md](prompts/update-feature.md) |
| Fix a bug | [fix-bug.md](prompts/fix-bug.md) |
| Update context after implementation | [learn-update.md](prompts/learn-update.md) |

**That's it!** You're using Context Mesh.

---

## The 3 Steps Explained

### 1. Intent - What and Why

Before coding, document what you're building and why.

**What you create:**
- `project-intent.md` - Overall project purpose
- `feature-*.md` - What each feature does
- `decisions/*.md` - Technical decisions (ADR)

**Use prompts:** `new-project.md`, `add-feature.md`, `update-feature.md`, `fix-bug.md`

### 2. Build - AI Generates, Human Supervises

Build with AI using your documented context.

**Key rule:** Create technical decision (ADR) before implementing.

**How to build:**
```
Implement [feature] following @context/intent/feature-[name].md
and @context/decisions/[number]-[decision].md
```

The AI reads your context and generates code that follows your decisions.

### 3. Learn - Update Context

After implementation, update context to reflect what actually happened.

**What you update:**
- Mark features/bugs as complete
- Add outcomes to decisions
- Document learnings
- Update changelog

**Use prompt:** `learn-update.md`

---

## Folder Structure

Context Mesh creates this structure:

```
your-project/
├── context/
│   ├── intent/           # What and why
│   │   ├── project-intent.md
│   │   ├── feature-*.md
│   │   └── bug-*.md
│   ├── decisions/        # Technical decisions (ADR)
│   │   └── 001-*.md, 002-*.md, ...
│   ├── knowledge/        # Patterns and anti-patterns
│   │   ├── patterns/
│   │   └── anti-patterns/
│   ├── agents/           # Reusable execution patterns (optional)
│   │   └── agent-*.md
│   └── evolution/        # Changes and learnings
│       ├── changelog.md
│       └── learning-*.md
└── [your code]
```

---

## Daily Workflow

```
┌─────────────────────────────────────────┐
│  1. INTENT                              │
│     Need to build something?            │
│     → Use add-feature.md or fix-bug.md  │
│     → Create decision (ADR) if needed   │
└─────────────────┬───────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│  2. BUILD                               │
│     Ready to code?                      │
│     → Reference context files in prompt │
│     → AI generates, you supervise       │
└─────────────────┬───────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│  3. LEARN                               │
│     Done implementing?                  │
│     → Use learn-update.md               │
│     → Mark complete, add learnings      │
└─────────────────┬───────────────────────┘
                  ↓
           Back to Intent
```

---

## Example: Adding a Feature

**1. Intent** - Use `add-feature.md` prompt:
- Creates `context/intent/feature-user-auth.md`
- Creates `context/decisions/002-auth-approach.md`

**2. Build** - Prompt the AI:
```
Implement user authentication following @context/intent/feature-user-auth.md
and @context/decisions/002-auth-approach.md
```

**3. Learn** - Use `learn-update.md` prompt:
- Marks feature as complete
- Adds outcomes to decision
- Updates changelog

---

## Tips

1. **Keep it simple** - Don't over-document, focus on what matters
2. **Decision before code** - Always create ADR before implementing
3. **Update as you go** - Keep context aligned with reality
4. **Use simple prompts** - Reference context files, don't repeat details

---

## All Prompts

| Scenario | Prompt | When to use |
|----------|--------|-------------|
| New project | [new-project.md](prompts/new-project.md) | Starting fresh |
| Existing project | [existing-project.md](prompts/existing-project.md) | Adding to existing code |
| Client project | [freelance-project.md](prompts/freelance-project.md) | Freelance work |
| Add feature | [add-feature.md](prompts/add-feature.md) | New functionality |
| Update feature | [update-feature.md](prompts/update-feature.md) | Changing existing feature |
| Fix bug | [fix-bug.md](prompts/fix-bug.md) | Bug fixes |
| After implementation | [learn-update.md](prompts/learn-update.md) | Completing work |
| Create agent | [create-agent.md](prompts/create-agent.md) | Reusable execution pattern |

---

## Next Steps

- **Need more details?** See [FRAMEWORK.md](FRAMEWORK.md)
- **See examples?** Check [examples/](examples/)
- **Common questions?** See [FAQ.md](FAQ.md)
