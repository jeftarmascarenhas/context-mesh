# AGENTS.md - Todo App Example

This `AGENTS.md` file demonstrates how AGENTS.md integrates with Context Mesh. It acts as a **succinct router** that directs AI agents to Context Mesh files for strategic context while providing essential operational instructions.

> **Note**: This is an example for the Todo App. See [AGENTS.md website](https://agents.md/) for the standard format.
> 
> **Important**: Keep this file updated when context changes to maintain accurate routing for AI agents and ensure the living context stays synchronized.

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
- Run tests: `npm test` (watch mode) or `npm test -- --coverage` (with coverage)
- Build for production: `npm run build`

### Testing
- Backend tests: `cd backend && npm test` (watch) or `npm test -- --coverage`
- Frontend tests: `cd frontend && npm test` (watch) or `npm test -- --coverage`
- Coverage target: Minimum 70% (branches, functions, lines, statements)
- See `@context/decisions/005-testing-strategy.md` for testing patterns

### CI/CD
- Test workflows locally: `act -W .github/workflows/backend.yml` (requires `act` installed)
- Workflows run automatically on push and PR
- Backend deploys to Railway on push to `main` (if CI passes)
- Frontend deploys to Vercel on push to `main` (if CI passes)
- See `@context/decisions/006-ci-cd-pipeline.md` for CI/CD details

### Database
- Start PostgreSQL: `docker-compose up -d` (uses Docker Compose)
- Stop PostgreSQL: `docker-compose down`
- View logs: `docker-compose logs -f postgres`
- Reset database: `docker-compose down -v && docker-compose up -d`
- Connection string: `DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp`
- See `@context/decisions/004-dev-environment.md` for details

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

**This is the key integration point with Context Mesh. Keep this section updated when context changes.**

When working on this project, AI agents should load relevant Context Mesh files:

**Always load:**
- `@context/intent/project-intent.md`

**Load as needed:**
- `@context/decisions/001-tech-stack.md`
- `@context/decisions/002-auth-approach.md`
- `@context/decisions/003-database-schema.md`
- `@context/decisions/004-dev-environment.md`
- `@context/decisions/005-testing-strategy.md`
- `@context/decisions/006-ci-cd-pipeline.md`
- `@context/decisions/007-deployment-platforms.md`
- `@context/knowledge/patterns/*.md`
- `@context/knowledge/anti-patterns/*.md`
- `@context/intent/feature-*.md` (when working on specific features)
- `@context/evolution/changelog.md` (when needed)

**How to use**: Load relevant Context Mesh files to understand strategic context before executing tasks. All details are in the context files - this file just routes you there.

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

1. **Load Context**: Load relevant Context Mesh files (see "Context Files to Load" above)
2. **Follow Context Mesh**: Intent → Build → Learn
3. **Execute**: Use simple prompts referencing Context Mesh files, run tests, update context if needed

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

### Critical: Always Update Context After Changes

**IMPORTANT**: After implementing, creating, or modifying code, AI agents MUST update Context Mesh:

1. **After creating new files/modules**:
   - Update relevant feature intent if scope changed
   - Create or update decision if new technical approach was used
   - Update changelog.md

2. **After modifying existing code**:
   - Update feature intent if functionality changed
   - Update decision outcomes if approach differed from plan
   - Update changelog.md

3. **After completing work**:
   - Mark feature/bug as completed in intent file
   - Add outcomes to decision files
   - Document learnings in evolution/learning-*.md
   - Update changelog.md

**How to update context:**
- After implementation, update relevant Context Mesh files:
  - Mark feature/bug as completed in intent file
  - Add outcomes to decision files
  - Update changelog.md
  - Document learnings if significant
- You can use AI to help identify what needs updating

**Never leave context stale** - Context Mesh only works if context reflects reality.

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

See Context Mesh files for details:
- Backend patterns: `@context/knowledge/patterns/api-design.md`
- Anti-patterns: `@context/knowledge/anti-patterns/avoid-direct-db.md`
- Tech stack: `@context/decisions/001-tech-stack.md`

---

## Definition of Done (Project/Feature Level)

This is the **project-level DoD** that every feature must meet before being considered complete. This is different from:
- **Success Criteria**: Functional requirements in `feature-*.md` (acceptance criteria)

Before completing a feature:
- [ ] Technical decision (ADR) verified or created before implementation - **Required**
- [ ] Code follows patterns from Context Mesh
- [ ] Decisions from Context Mesh are respected
- [ ] Tests passing (70% coverage minimum)
- [ ] **Context updated** - Context Mesh files updated to reflect implementation (Context Mesh requirement)
- [ ] Feature/bug marked as completed in intent file
- [ ] Decision outcomes added (if applicable)
- [ ] Changelog updated
- [ ] Code linked to relevant intent/decisions
- [ ] Success Criteria met (from `feature-*.md` - acceptance criteria)

---

## Common Mistakes to Avoid

| Mistake | Why it's bad | Context Mesh Reference |
|---------|--------------|------------------------|
| Ignoring decisions | Breaks architecture | @context/decisions/ |
| Using anti-patterns | Creates technical debt | @context/knowledge/anti-patterns/ |
| **Not updating context after changes** | **Context becomes stale, breaks Context Mesh** | **Always update context after implementation** |
| Creating files without updating context | Context doesn't reflect reality | Always update after implementation |
| Skipping tests | Reduces quality | @context/knowledge/patterns/testing.md |
| Skipping ADR before implementation | Breaks decision architecture | Always create decision before implementing |

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

**Example - Docker Compose:**
```
Create docker-compose.yml following @context/decisions/004-dev-environment.md
and @context/knowledge/patterns/docker-compose.md
```

**Example - Testing:**
```
Implement unit tests following @context/intent/feature-testing.md
and @context/decisions/005-testing-strategy.md
```

**Example - CI/CD:**
```
Create GitHub Actions workflows following @context/intent/feature-ci-cd.md
and @context/decisions/006-ci-cd-pipeline.md
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
DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp
JWT_SECRET=your-secret-key-here
JWT_EXPIRES_IN=7d
PORT=3000
NODE_ENV=development
```

**Production (Railway)**:
- Set in Railway dashboard
- `DATABASE_URL` auto-set by Railway PostgreSQL
- `JWT_SECRET` must be set manually (generate secure secret)

### Frontend (.env)
```
VITE_API_URL=http://localhost:3000/api/v1
```

**Production (Vercel)**:
- Set in Vercel dashboard
- `VITE_API_URL` should point to Railway backend URL

### CI/CD Secrets (GitHub)
Configure in GitHub repository settings (Settings → Secrets and variables → Actions):
- `RAILWAY_TOKEN` - Railway API token (for backend deployment)
- `VERCEL_TOKEN` - Vercel API token (for frontend deployment)
- `VERCEL_ORG_ID` - Vercel organization ID
- `VERCEL_PROJECT_ID` - Vercel project ID
- `VITE_API_URL` - Frontend API URL (for build)

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

