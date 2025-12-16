# AGENTS.md - Weather App Minimal

> **For AI Agents**: This project follows the **Context Mesh** framework.
> Before writing any code, you MUST load and understand the context files.

---

## 🧠 Context Mesh Framework

This project uses [Context Mesh](https://github.com/jeftarmascarenhas/context-mesh) for AI-First development.

**Workflow**: Intent → Build → Learn

1. **Intent** (Step 1): Understand WHAT and WHY before coding
2. **Build** (Step 2): Implement following decisions and patterns
3. **Learn** (Step 3): Update context after implementation

---

## 📂 Context Structure

```
context/
├── intent/
│   ├── project-intent.md          # Project vision and goals
│   └── feature-weather-display.md # Weather feature requirements
├── decisions/
│   ├── 001-tech-stack.md          # Vite, Fastify, shadcn-ui
│   └── 002-api-integration.md     # Open-Meteo API
├── knowledge/patterns/
│   ├── api-design.md              # API patterns
│   └── component-structure.md     # React component patterns
├── agents/
│   ├── agent-setup.md             # Phase 1: Project structure
│   ├── agent-backend.md           # Phase 2: Weather API
│   └── agent-frontend.md          # Phase 3: React UI
└── evolution/
    └── changelog.md               # Project history
```

---

## 🚀 Quick Start

```bash
# Backend
cd backend && pnpm install && pnpm run dev
# → http://localhost:3000/docs (Swagger)

# Frontend
cd frontend && pnpm install && pnpm run dev
# → http://localhost:5173
```

---

## 🤖 AI Agent Instructions

### Before Any Implementation

1. **Load project intent**: `@context/intent/project-intent.md`
2. **Load feature intent**: `@context/intent/feature-weather-display.md`
3. **Load decisions**: `@context/decisions/001-tech-stack.md`, `@context/decisions/002-api-integration.md`
4. **Load patterns**: `@context/knowledge/patterns/*.md`

### During Implementation

1. **Execute the agent**: `@context/agents/agent-*.md` for the current phase
2. **Follow patterns**: Use patterns from `@context/knowledge/patterns/`
3. **Respect decisions**: All technical choices are documented in `@context/decisions/`

### After Implementation

1. **Mark feature as completed** in the intent file
2. **Add outcomes** to decision files (what worked, what didn't)
3. **Update changelog.md** with what changed

---

## 📋 Execution Agents

Execute phases in order. Each agent has its own **Definition of Done**.

| Phase | Agent | Purpose |
|-------|-------|---------|
| 1 | @context/agents/agent-setup.md | Project structure |
| 2 | @context/agents/agent-backend.md | Weather API (Open-Meteo) |
| 3 | @context/agents/agent-frontend.md | React UI (shadcn-ui) |

> 📖 See [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) for step-by-step instructions.

---

## 📚 Context Files to Load

**Always load (before any work):**
- `@context/intent/project-intent.md` - Project vision and constraints

**Load per feature:**
- `@context/intent/feature-weather-display.md` - Weather feature requirements

**Load per phase:**
- `@context/agents/agent-*.md` - Execution steps (has Definition of Done)
- `@context/decisions/*.md` - Technical decisions
- `@context/knowledge/patterns/*.md` - Patterns to follow

---

## ⚙️ Environment Variables

**backend/.env**
```
PORT=3000
```

**Note**: No API key required! Open-Meteo is free and open source.

---

## ✅ Definition of Done (Technical/Build Phase)

Definition of Done is defined in each **agent file** (`agent-*.md`).

General checklist:
- [ ] Code follows patterns from `@context/knowledge/patterns/`
- [ ] Server starts without errors
- [ ] Swagger docs accessible at `/docs` (backend)
- [ ] UI renders correctly (frontend)
- [ ] Agent's Definition of Done is complete

---

## ⚠️ AI Agent Rules

### ✅ ALWAYS
- Load context files before implementing
- Follow decisions from `@context/decisions/`
- Use patterns from `@context/knowledge/patterns/`
- Update context after implementation
- Add Swagger documentation for all endpoints

### ❌ NEVER
- Ignore documented decisions
- Skip Swagger documentation
- Leave context stale after implementation
- Skip loading intent files
- Implement without understanding the WHY

---

## 🔄 Context Update (Critical)

After completing any feature:

```markdown
1. Update @context/intent/feature-weather-display.md
   - Mark as completed
   - Add any learnings

2. Update @context/decisions/*.md
   - Add outcomes section
   - Document what worked/didn't

3. Update @context/evolution/changelog.md
   - What changed
   - Why it changed
```

**Never leave context stale. Future AI sessions depend on accurate context.**

---

## 🎨 Code Style

- TypeScript strict mode
- Fastify with Swagger
- React functional components
- shadcn-ui for UI components
- Follow patterns from `@context/knowledge/patterns/`

---

## 📖 References

- [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) - Step-by-step execution
- [Context Mesh Framework](https://github.com/jeftarmascarenhas/context-mesh)
- [Framework Documentation](../../FRAMEWORK.md)
- [AGENTS.md Standard](https://agents.md/)
