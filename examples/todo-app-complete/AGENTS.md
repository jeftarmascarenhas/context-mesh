# AGENTS.md - Todo App Example

This `AGENTS.md` file demonstrates how AGENTS.md integrates with Context Mesh. It acts as a **router** that references Context Mesh files for strategic context while providing operational instructions for building the Todo application.

> **Note**: This is an example for the Todo App. See [AGENTS.md website](https://agents.md/) for the standard format.

---

## Setup Commands

### Backend
- Install dependencies: `cd backend && npm install`
- Start dev server: `npm run dev`
- Run migrations: `npx prisma migrate dev`
- Generate Prisma client: `npx prisma generate`
- Run tests: `npm test`

### Frontend
- Install dependencies: `cd frontend && npm install`
- Start dev server: `npm run dev`
- Run tests: `npm test`
- Build for production: `npm run build`

### Database
- Start PostgreSQL: `docker-compose up -d` (if using Docker)
- Or use local PostgreSQL instance
- Connection string: `DATABASE_URL=postgresql://user:password@localhost:5432/todoapp`

---

## Code Style

- **TypeScript**: Strict mode enabled
- **Backend**: Express with TypeScript, use service layer pattern
- **Frontend**: React with TypeScript, functional components
- **Formatting**: ESLint + Prettier
- **Quotes**: Single quotes preferred
- **Semicolons**: Optional (follow project preference)

---

## Context Files to Load

**This is the key integration point with Context Mesh.**

When working on this project, AI agents **must** load Context Mesh files for strategic context:

### Project Overview (Always Load)
- `@context/intent/project-intent.md` - Overall project goals, scope, and success criteria

### Technical Decisions (Load as Needed)
- `@context/decisions/001-tech-stack.md` - Technology stack (React, Express, Prisma, PostgreSQL)
- `@context/decisions/002-auth-approach.md` - Authentication approach (JWT, bcrypt, httpOnly cookies)
- `@context/decisions/003-database-schema.md` - Database schema (Prisma models)

### Knowledge and Patterns (Load as Needed)
- `@context/knowledge/patterns/api-design.md` - API design pattern (endpoints, request/response format)
- `@context/knowledge/anti-patterns/avoid-direct-db.md` - Anti-pattern to avoid (service layer pattern)

### Feature-Specific Context (Load When Working on Feature)
- `@context/intent/feature-user-auth.md` - User authentication requirements
- `@context/intent/feature-todo-crud.md` - Todo CRUD requirements
- `@context/intent/bug-todo-persistence.md` - Bug fix requirements (if fixing bugs)

### Evolution (Reference When Needed)
- `@context/evolution/changelog.md` - Project changelog
- `@context/evolution/learning-001-auth.md` - Learnings from authentication implementation

**How to use**: When an AI agent starts working, it should load the relevant Context Mesh files above to understand the strategic context (what, why, how decided) before executing operational tasks.

---

## Project Structure

```
todo-app/
├── AGENTS.md              # This file (router for AI agents)
├── context/               # Context Mesh: strategic context
│   ├── intent/
│   │   ├── project-intent.md
│   │   ├── feature-user-auth.md
│   │   ├── feature-todo-crud.md
│   │   └── bug-todo-persistence.md
│   ├── decisions/
│   │   ├── 001-tech-stack.md
│   │   ├── 002-auth-approach.md
│   │   └── 003-database-schema.md
│   ├── knowledge/
│   │   ├── patterns/
│   │   │   └── api-design.md
│   │   └── anti-patterns/
│   │       └── avoid-direct-db.md
│   └── evolution/
│       ├── changelog.md
│       └── learning-001-auth.md
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── middleware/
│   │   ├── dto/
│   │   └── app.ts
│   ├── prisma/
│   │   ├── schema.prisma
│   │   └── migrations/
│   └── package.json
└── frontend/
    ├── src/
    │   ├── components/
    │   ├── pages/
    │   ├── services/
    │   └── App.tsx
    └── package.json
```

---

## Development Workflow

### Step 1: Load Context (Context Mesh Integration)

Before starting work, load relevant Context Mesh files:

**Always load:**
- `@context/intent/project-intent.md` - Project overview

**Load based on task:**
- Working on auth? → `@context/intent/feature-user-auth.md` + `@context/decisions/002-auth-approach.md`
- Working on todos? → `@context/intent/feature-todo-crud.md` + `@context/decisions/003-database-schema.md`
- Working on API? → `@context/knowledge/patterns/api-design.md`
- Avoiding mistakes? → `@context/knowledge/anti-patterns/avoid-direct-db.md`

### Step 2: Follow Context Mesh Workflow

1. **Intent**: Understand what to build (from Context Mesh)
2. **Build**: Generate code following patterns and decisions from Context Mesh
3. **Learn**: Update context after changes (if implementation differs from plan)

### Step 3: Execute

- Follow code style and conventions
- Use **simple prompts** that reference Context Mesh files (see README.md)
- Run tests before committing
- Update context if implementation differs from plan

---

## Testing Instructions

### Backend Tests
- Run all tests: `cd backend && npm test`
- Run specific test: `npm test -t "test name"`
- Run with coverage: `npm test -- --coverage`

### Frontend Tests
- Run all tests: `cd frontend && npm test`
- Run in watch mode: `npm test -- --watch`

### Integration Tests
- Ensure backend is running: `cd backend && npm run dev`
- Ensure frontend is running: `cd frontend && npm run dev`
- Test end-to-end flows manually

---

## AI Agent Behavior

### Allowed

- Create/edit code following Context Mesh patterns
- Reference decisions from `@context/decisions/`
- Follow patterns from `@context/knowledge/patterns/`
- Avoid anti-patterns from `@context/knowledge/anti-patterns/`
- Update context when implementation differs from plan
- Use **simple prompts** that reference Context Mesh files

### Forbidden

- Modifying `package.json` or config files without explicit instruction
- Ignoring decisions from `@context/decisions/`
- Using anti-patterns from `@context/knowledge/anti-patterns/` (e.g., direct DB access in routes)
- Changing project structure without updating context
- Writing detailed prompts that duplicate context information

---

## Architecture Overview

See `@context/decisions/001-tech-stack.md` for complete technology stack.

**Key Technologies:**
- **Frontend**: React 18+ with TypeScript, Vite, React Router, Axios
- **Backend**: Node.js with Express, TypeScript, Prisma ORM
- **Database**: PostgreSQL with Prisma
- **Authentication**: JWT with httpOnly cookies (see `@context/decisions/002-auth-approach.md`)
- **API Design**: RESTful API following `@context/knowledge/patterns/api-design.md`

---

## Coding Conventions

### Backend

- **Service Layer Pattern**: Always use service layer, never access Prisma directly from routes
  - See: `@context/knowledge/anti-patterns/avoid-direct-db.md`
- **DTOs**: Use DTOs with validation (class-validator)
- **Error Handling**: Use error middleware
- **Authentication**: JWT middleware for protected routes
- **API Format**: Follow `@context/knowledge/patterns/api-design.md`

### Frontend

- **Components**: Functional components with TypeScript
- **State Management**: React hooks (useState, useContext)
- **API Calls**: Use Axios service (see `services/api.ts`)
- **Routing**: React Router with protected routes
- **Authentication**: Auth context/provider for managing auth state

---

## Definition of Done

Before completing work:

- [ ] Code follows patterns from Context Mesh
- [ ] Decisions from Context Mesh are respected
- [ ] Service layer pattern used (no direct DB access in routes)
- [ ] API follows pattern from `@context/knowledge/patterns/api-design.md`
- [ ] Tests passing
- [ ] Linter passing
- [ ] Context updated if implementation differs from plan
- [ ] Code linked to relevant intent/decisions

---

## Common Mistakes to Avoid

| Mistake | Why it's bad | Context Mesh Reference |
|---------|--------------|----------------------|
| Direct DB access in routes | Breaks architecture, hard to test | `@context/knowledge/anti-patterns/avoid-direct-db.md` |
| Ignoring API pattern | Inconsistent API responses | `@context/knowledge/patterns/api-design.md` |
| Not using service layer | Violates architecture decision | `@context/knowledge/anti-patterns/avoid-direct-db.md` |
| Not updating context | Context becomes stale | Context Mesh principle |
| Skipping tests | Reduces quality | Project success criteria |
| Detailed prompts | Duplicates context | Context Mesh philosophy |

---

## Simple Prompts (Recommended)

Since context is primary, use simple prompts that reference Context Mesh:

**Example - Setup:**
```
Create the project structure following @context/decisions/001-tech-stack.md
and @context/decisions/003-database-schema.md
```

**Example - Authentication:**
```
Implement authentication following @context/intent/feature-user-auth.md
and @context/decisions/002-auth-approach.md
```

**Example - Todo CRUD:**
```
Implement Todo CRUD following @context/intent/feature-todo-crud.md
```

See [README.md](README.md) for more prompt examples.

---

## Integration with Context Mesh

**AGENTS.md** (this file) provides:
- ✅ Operational instructions (setup, commands, conventions)
- ✅ Router to Context Mesh files
- ✅ Development workflow
- ✅ Code style and conventions

**Context Mesh** provides:
- ✅ Strategic context (intent, decisions, knowledge)
- ✅ Living context that evolves
- ✅ Full traceability
- ✅ Patterns and anti-patterns

**Together**: Complete guidance for AI agents - both operational (how) and strategic (what, why).

---

## Environment Variables

### Backend (.env)
```
DATABASE_URL=postgresql://user:password@localhost:5432/todoapp
JWT_SECRET=your-secret-key-here
JWT_EXPIRES_IN=7d
PORT=3000
NODE_ENV=development
```

### Frontend (.env)
```
VITE_API_URL=http://localhost:3000/api/v1
```

---

## References

- [Context Mesh Framework](../../FRAMEWORK.md) - Framework documentation
- [AGENTS.md Standard](https://agents.md/) - AGENTS.md format specification
- [README.md](README.md) - Complete example guide with prompts
- Context Mesh files in `context/` directory

---

**Last Updated**: 2024-01-20  
**Project**: Todo App Example  
**AI Collaborator**: Cursor / GitHub Copilot / etc.

