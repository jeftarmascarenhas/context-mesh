# AGENTS.md - Todo App Example

Router for AI agents. Directs to Context Mesh files for strategic context.

> See [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) for step-by-step instructions.

---

## Quick Start

```bash
# Start database
docker-compose up -d

# Backend
cd backend && pnpm install && pnpm run dev

# Frontend
cd frontend && pnpm install && pnpm run dev
```

---

## Execution Agents

Execute in order:

| Phase | Agent | Purpose |
|-------|-------|---------|
| 1 | @context/agents/agent-setup.md | Project structure |
| 2 | @context/agents/agent-database.md | PostgreSQL + Prisma |
| 3 | @context/agents/agent-auth.md | Authentication |
| 4 | @context/agents/agent-todo.md | Todo CRUD |
| 5 | @context/agents/agent-frontend.md | React UI |
| 6 | @context/agents/agent-testing.md | Tests (optional) |
| 7 | @context/agents/agent-cicd.md | CI/CD (optional) |

---

## Context Files

**Always load:**
- @context/intent/project-intent.md

**Load as needed:**
- @context/decisions/*.md - Technical decisions
- @context/knowledge/patterns/*.md - Patterns to follow
- @context/knowledge/anti-patterns/*.md - What to avoid
- @context/intent/feature-*.md - Feature requirements

---

## Commands

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

## Environment Variables

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

## Code Style

- TypeScript strict mode
- Service layer pattern (no direct DB in routes)
- Functional React components
- ESLint + Prettier

---

## AI Behavior

### Allowed
- Reference decisions from @context/decisions/
- Follow patterns from @context/knowledge/patterns/
- Update context after implementation

### Forbidden
- Direct DB access in routes
- Ignoring decisions
- Leaving context stale

---

## Definition of Done

Before completing a phase:
- [ ] Code follows context patterns
- [ ] Build passes: `pnpm run build`
- [ ] Tests pass (if applicable)
- [ ] Context updated if needed

---

## References

- [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) - Execution steps
- [Framework Documentation](../../FRAMEWORK.md)
- [AGENTS.md Standard](https://agents.md/)
