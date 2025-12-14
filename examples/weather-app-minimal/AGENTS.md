# AGENTS.md - Weather App Minimal Example

This `AGENTS.md` file demonstrates how AGENTS.md integrates with Context Mesh. It acts as a **succinct router** that directs AI agents to Context Mesh files for strategic context while providing essential operational instructions.

> **Note**: This is an example for the Weather App Minimal. See [AGENTS.md website](https://agents.md/) for the standard format.
> 
> **Important**: Keep this file updated when context changes to maintain accurate routing for AI agents and ensure the living context stays synchronized.

---

## Setup Commands

### Backend
- Install dependencies: `cd backend && npm install`
- Start dev server: `npm run dev` (runs on port 3000)
- View Swagger docs: http://localhost:3000/docs

### Frontend
- Install dependencies: `cd frontend && npm install`
- Initialize shadcn-ui: `npx shadcn-ui@latest init`
- Add shadcn-ui components: `npx shadcn-ui@latest add button card input`
- Start dev server: `npm run dev` (runs on port 5173)

### Environment Variables

**Backend (.env)**:
```
OPENWEATHER_API_KEY=your_api_key_here
PORT=3000
```

Get API key from: https://openweathermap.org/api (free tier)

---

## Code Style

- **TypeScript**: Strict mode enabled
- **Backend**: Fastify with TypeScript, service layer pattern
- **Frontend**: React with TypeScript, functional components, shadcn-ui
- **Formatting**: ESLint + Prettier (optional)
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
- `@context/decisions/002-api-integration.md`
- `@context/knowledge/patterns/*.md`
- `@context/intent/feature-weather-display.md` (when working on weather feature)
- `@context/evolution/changelog.md` (when needed)

**How to use**: Load relevant Context Mesh files to understand strategic context before executing tasks. All details are in the context files - this file just routes you there.

---

## Project Structure

```
weather-app-minimal/
├── AGENTS.md              # This file (router for AI agents)
├── context/               # Context Mesh: strategic context
│   ├── intent/
│   │   ├── project-intent.md
│   │   └── feature-weather-display.md
│   ├── decisions/
│   │   ├── 001-tech-stack.md
│   │   └── 002-api-integration.md
│   ├── knowledge/
│   │   └── patterns/
│   │       ├── api-design.md
│   │       └── component-structure.md
│   └── evolution/
│       └── changelog.md
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   │   └── weather.routes.ts
│   │   ├── services/
│   │   │   └── weather.service.ts
│   │   ├── plugins/
│   │   │   ├── swagger.ts
│   │   │   └── cors.ts
│   │   └── app.ts
│   ├── .env
│   ├── .env.example
│   └── package.json
└── frontend/
    ├── src/
    │   ├── components/
    │   │   ├── ui/              # shadcn-ui components
    │   │   ├── WeatherCard.tsx
    │   │   ├── WeatherForm.tsx
    │   │   └── WeatherDisplay.tsx
    │   ├── services/
    │   │   └── api.ts
    │   ├── types/
    │   │   └── weather.ts
    │   ├── App.tsx
    │   └── main.tsx
    ├── package.json
    └── vite.config.ts
```

---

## Development Workflow

1. **Load Context**: Load relevant Context Mesh files (see "Context Files to Load" above)
2. **Follow Context Mesh**: Intent → Build → Learn
3. **Execute**: Use simple prompts referencing Context Mesh files, run tests, update context if needed

---

## AI Agent Behavior

### Allowed

- Create/edit code following Context Mesh patterns
- Reference decisions from `@context/decisions/`
- Follow patterns from `@context/knowledge/patterns/`
- Use **simple prompts** that reference Context Mesh files
- Update context when implementation differs from plan

### Forbidden

- Modifying `package.json` or config files without explicit instruction
- Ignoring decisions from `@context/decisions/`
- Using patterns not in `@context/knowledge/patterns/`
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

## Architecture & Conventions

See Context Mesh files for details:
- Tech stack: `@context/decisions/001-tech-stack.md`
- API integration: `@context/decisions/002-api-integration.md`
- Patterns: `@context/knowledge/patterns/*.md`

---

## Definition of Done (Technical/Feature Level - Step 2: Build Only)

**Important**: DoD applies only to **Step 2 (Build)** when implementing features technically. Steps 1 (Intent) and 3 (Learn) don't have DoD - they have flexible "Outputs" instead.

This is the **technical/feature-level DoD** that every feature implementation must meet before being considered complete. This is different from:
- **Success Criteria**: Functional requirements in `feature-*.md` (acceptance criteria)

**When to apply**: Only during Step 2 (Build) when implementing code, not during Step 1 (Intent) or Step 3 (Learn).

Before completing a feature implementation (Step 2 - Build):
- [ ] Technical decision (ADR) verified or created before implementation - **Required**
- [ ] Code follows patterns from Context Mesh
- [ ] Decisions from Context Mesh are respected
- [ ] Code runs without errors
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
| Skipping ADR before implementation | Breaks decision architecture | Always create decision before implementing |

---

## Simple Prompts (Recommended)

Since context is primary, use simple prompts that reference Context Mesh:

**Example - Backend Setup:**
```
Create the backend project structure following @context/decisions/001-tech-stack.md
Setup Swagger documentation following @context/knowledge/patterns/api-design.md
```

**Example - Weather Service:**
```
Implement weather service following @context/decisions/002-api-integration.md
```

**Example - Weather Route:**
```
Create weather route following @context/intent/feature-weather-display.md
and @context/knowledge/patterns/api-design.md
```

**Example - Frontend Setup:**
```
Create the frontend project structure following @context/decisions/001-tech-stack.md
Setup shadcn-ui following @context/knowledge/patterns/component-structure.md
```

**Example - Weather Components:**
```
Create weather components following @context/intent/feature-weather-display.md
and @context/knowledge/patterns/component-structure.md
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
- ✅ Patterns and best practices

**Together**: Complete guidance for AI agents - both operational (how) and strategic (what, why).

---

## Environment Variables

### Backend (.env)
```
OPENWEATHER_API_KEY=your_api_key_here
PORT=3000
```

**Get API Key**: https://openweathermap.org/api (free tier: 1,000 calls/day)

### Frontend
No environment variables needed (uses backend URL directly)

---

## References

- [Context Mesh Framework](../../FRAMEWORK.md) - Framework documentation
- [AGENTS.md Standard](https://agents.md/) - AGENTS.md format specification
- [README.md](README.md) - Complete example guide with prompts
- Context Mesh files in `context/` directory

---

**Last Updated**: 2024-01-20  
**Project**: Weather App Minimal Example  
**AI Collaborator**: Cursor / GitHub Copilot / etc.

