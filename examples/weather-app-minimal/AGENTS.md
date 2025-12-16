# AGENTS.md - Weather App Minimal

Router for AI agents. Directs to Context Mesh files for strategic context.

> See [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) for step-by-step instructions.

---

## Quick Start

```bash
# Backend
cd backend && pnpm install && pnpm run dev
# → http://localhost:3000/docs (Swagger)

# Frontend
cd frontend && pnpm install && pnpm run dev
# → http://localhost:5173
```

---

## Execution Agents

Execute in order:

| Phase | Agent | Purpose |
|-------|-------|---------|
| 1 | @context/agents/agent-setup.md | Project structure |
| 2 | @context/agents/agent-backend.md | Weather API |
| 3 | @context/agents/agent-frontend.md | React UI |

---

## Context Files

**Always load:**
- @context/intent/project-intent.md

**Load as needed:**
- @context/decisions/001-tech-stack.md
- @context/decisions/002-api-integration.md
- @context/knowledge/patterns/*.md
- @context/intent/feature-weather-display.md

---

## Commands

### Backend
```bash
pnpm install
pnpm run dev
```

### Frontend
```bash
pnpm install
pnpm run dev
```

---

## Environment Variables

**backend/.env**
```
PORT=3000
```

**Note**: No API key required! Open-Meteo is free and open source.

---

## Code Style

- TypeScript strict mode
- Fastify with Swagger
- React functional components
- shadcn-ui for UI components

---

## AI Behavior

### Allowed
- Reference decisions from @context/decisions/
- Follow patterns from @context/knowledge/patterns/
- Update context after implementation

### Forbidden
- Ignoring decisions
- Skipping Swagger documentation
- Leaving context stale

---

## Definition of Done

Before completing a phase:
- [ ] Code follows context patterns
- [ ] Server starts without errors
- [ ] Swagger docs accessible (backend)
- [ ] UI renders correctly (frontend)

---

## References

- [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) - Execution steps
- [Framework Documentation](../../FRAMEWORK.md)
- [AGENTS.md Standard](https://agents.md/)
