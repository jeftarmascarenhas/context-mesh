# AGENTS.md - Todo App Complete

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
│   └── feature-*.md               # Feature requirements
├── decisions/
│   └── 001-*.md                   # Technical decisions
├── knowledge/
│   ├── patterns/                  # Code patterns to FOLLOW
│   └── anti-patterns/             # What to AVOID
├── agents/
│   ├── agent-setup.md             # Phase 1: Project structure
│   ├── agent-database.md          # Phase 2: PostgreSQL + Prisma
│   ├── agent-auth.md              # Phase 3: Authentication
│   ├── agent-todo.md              # Phase 4: Todo CRUD
│   ├── agent-frontend.md          # Phase 5: React UI
│   ├── agent-testing.md           # Phase 6: Tests (optional)
│   └── agent-cicd.md              # Phase 7: CI/CD (optional)
└── evolution/
    └── changelog.md               # Project history
```

---

## 🚀 Quick Start

```bash
# Start database
docker-compose up -d

# Backend
cd backend && pnpm install && pnpm run dev

# Frontend
cd frontend && pnpm install && pnpm run dev
```

---

## 🤖 AI Agent Instructions

### Before Any Implementation

1. **Load project intent**: `@context/intent/project-intent.md`
2. **Load feature intent**: `@context/intent/feature-*.md` (for the feature you're implementing)
3. **Load decisions**: `@context/decisions/*.md` (relevant to the feature)
4. **Load patterns**: `@context/knowledge/patterns/*.md`

### During Implementation

1. **Execute the agent**: `@context/agents/agent-*.md` for the current phase
2. **Follow patterns**: Use patterns from `@context/knowledge/patterns/`
3. **Avoid anti-patterns**: Check `@context/knowledge/anti-patterns/`
4. **Respect decisions**: All technical choices are documented in `@context/decisions/`

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
| 2 | @context/agents/agent-database.md | PostgreSQL + Prisma |
| 3 | @context/agents/agent-auth.md | Authentication (JWT) |
| 4 | @context/agents/agent-todo.md | Todo CRUD |
| 5 | @context/agents/agent-frontend.md | React UI |
| 6 | @context/agents/agent-testing.md | Tests (optional) |
| 7 | @context/agents/agent-cicd.md | CI/CD (optional) |

> 📖 See [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) for step-by-step instructions.

---

## 📚 Context Files to Load

**Always load (before any work):**
- `@context/intent/project-intent.md` - Project vision and constraints

**Load per feature:**
- `@context/intent/feature-*.md` - Feature requirements (has Success Criteria)

**Load per phase:**
- `@context/agents/agent-*.md` - Execution steps (has Definition of Done)
- `@context/decisions/*.md` - Technical decisions
- `@context/knowledge/patterns/*.md` - Patterns to follow

---

## ⚙️ Commands

### Database
```bash
docker-compose up -d       # Start
docker-compose down        # Stop
docker-compose down -v     # Reset
```

### Backend
```bash
pnpm install
pnpm run dev
npx prisma migrate dev
npx prisma generate
pnpm test
```

### Frontend
```bash
pnpm install
pnpm run dev
pnpm test
pnpm run build
```

---

## ⚙️ Environment Variables

**backend/.env**
```
DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp
JWT_SECRET=your-secret-key-here
PORT=3000
```

**frontend/.env**
```
VITE_API_URL=http://localhost:3000/api/v1
```

---

## ✅ Definition of Done (Technical/Build Phase)

Definition of Done is defined in each **agent file** (`agent-*.md`).

General checklist:
- [ ] Code follows patterns from `@context/knowledge/patterns/`
- [ ] Build passes: `pnpm run build`
- [ ] Tests pass (if applicable)
- [ ] Agent's Definition of Done is complete

---

## ⚠️ AI Agent Rules

### ✅ ALWAYS
- Load context files before implementing
- Follow decisions from `@context/decisions/`
- Use patterns from `@context/knowledge/patterns/`
- Use service layer pattern (no direct DB in routes)
- Update context after implementation
- Check Definition of Done before completing a phase

### ❌ NEVER
- Direct database access in routes (use services)
- Ignore documented decisions
- Use patterns from `@context/knowledge/anti-patterns/`
- Leave context stale after implementation
- Skip loading intent files
- Implement without understanding the WHY

---

## 🔄 Context Update (Critical)

After completing any feature:

```markdown
1. Update @context/intent/feature-*.md
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
- Service layer pattern (no direct DB in routes)
- Functional React components
- ESLint + Prettier
- Follow patterns from `@context/knowledge/patterns/`

---

## 📖 References

- [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) - Step-by-step execution
- [Context Mesh Framework](https://github.com/jeftarmascarenhas/context-mesh)
- [Framework Documentation](../../FRAMEWORK.md)
- [AGENTS.md Standard](https://agents.md/)
