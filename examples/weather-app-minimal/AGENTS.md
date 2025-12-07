# AGENTS.md - Weather App Minimal Example

This `AGENTS.md` file demonstrates how AGENTS.md integrates with Context Mesh. It acts as a **router** that references Context Mesh files for strategic context while providing operational instructions for building the Weather application.

> **Note**: This is an example for the Weather App Minimal. See [AGENTS.md website](https://agents.md/) for the standard format.

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

**This is the key integration point with Context Mesh.**

When working on this project, AI agents **must** load Context Mesh files for strategic context:

### Project Overview (Always Load)
- `@context/intent/project-intent.md` - Overall project goals, scope, and success criteria

### Technical Decisions (Load as Needed)
- `@context/decisions/001-tech-stack.md` - Technology stack (Vite, Fastify, shadcn-ui)
- `@context/decisions/002-api-integration.md` - API integration (OpenWeatherMap)

### Knowledge and Patterns (Load as Needed)
- `@context/knowledge/patterns/api-design.md` - API design pattern (endpoints, request/response format)
- `@context/knowledge/patterns/component-structure.md` - Component structure pattern (React, shadcn-ui)

### Feature-Specific Context (Load When Working on Feature)
- `@context/intent/feature-weather-display.md` - Weather display requirements

### Evolution (Reference When Needed)
- `@context/evolution/changelog.md` - Project changelog

**How to use**: When an AI agent starts working, it should load the relevant Context Mesh files above to understand the strategic context (what, why, how decided) before executing operational tasks.

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

### Step 1: Load Context (Context Mesh Integration)

Before starting work, load relevant Context Mesh files:

**Always load:**
- `@context/intent/project-intent.md` - Project overview

**Load based on task:**
- Working on backend? → `@context/decisions/001-tech-stack.md` + `@context/decisions/002-api-integration.md` + `@context/knowledge/patterns/api-design.md`
- Working on frontend? → `@context/decisions/001-tech-stack.md` + `@context/knowledge/patterns/component-structure.md` + `@context/intent/feature-weather-display.md`
- Working on API? → `@context/knowledge/patterns/api-design.md` + `@context/decisions/002-api-integration.md`

### Step 2: Follow Context Mesh Workflow

1. **Intent**: Understand what to build (from Context Mesh)
2. **Build**: Generate code following patterns and decisions from Context Mesh
3. **Learn**: Update context after changes (if implementation differs from plan)

### Step 3: Execute

- Follow code style and conventions
- Use **simple prompts** that reference Context Mesh files (see README.md)
- Run and test before completing
- Update context if implementation differs from plan

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

---

## Architecture Overview

See `@context/decisions/001-tech-stack.md` for complete technology stack.

**Key Technologies:**
- **Frontend**: Vite + React 18+ with TypeScript, shadcn-ui, Tailwind CSS
- **Backend**: Node.js 20+ with Fastify, TypeScript, Swagger
- **API**: OpenWeatherMap (see `@context/decisions/002-api-integration.md`)
- **API Design**: RESTful API following `@context/knowledge/patterns/api-design.md`

---

## Coding Conventions

### Backend

- **Service Layer Pattern**: Use service layer for business logic
- **Fastify Plugins**: Use plugins for Swagger, CORS
- **Error Handling**: Follow API design pattern
- **API Format**: Follow `@context/knowledge/patterns/api-design.md`
- **Swagger**: Document all endpoints

### Frontend

- **Components**: Functional components with TypeScript
- **State Management**: React hooks (useState)
- **API Calls**: Use Axios service (see `services/api.ts`)
- **UI Components**: Use shadcn-ui components
- **Styling**: Tailwind CSS (via shadcn-ui)

---

## Definition of Done

Before completing work:

- [ ] Code follows patterns from Context Mesh
- [ ] Decisions from Context Mesh are respected
- [ ] API follows pattern from `@context/knowledge/patterns/api-design.md`
- [ ] Components follow pattern from `@context/knowledge/patterns/component-structure.md`
- [ ] Code runs without errors
- [ ] Context updated if implementation differs from plan
- [ ] Code linked to relevant intent/decisions

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

