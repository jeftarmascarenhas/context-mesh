# Agent: Setup - Weather App

## Purpose
Initialize the project structure with backend (Fastify) and frontend (Vite + React) configurations.

## Context Files to Load
- @context/intent/project-intent.md
- @context/decisions/001-tech-stack.md
- @context/decisions/002-api-integration.md

## Scope
- **Allowed directories:** Root project, `backend/`, `frontend/`
- **Prohibited:** Don't implement features yet, only infrastructure

## Execution Steps

1. **Create Backend Structure**
   - Initialize Node.js project with TypeScript
   - Configure Fastify with Swagger
   - Setup CORS plugin
   - Create `.env.example` with `PORT` (no API key needed for Open-Meteo)

2. **Create Frontend Structure**
   - Initialize Vite + React + TypeScript project
   - Configure Tailwind CSS
   - Initialize shadcn-ui
   - Add base components: button, card, input

3. **Create Project Root Files**
   - Create root `package.json` with workspace scripts
   - Create `.gitignore`

## Expected Output

```
weather-app-minimal/
├── backend/
│   ├── src/
│   │   ├── app.ts
│   │   └── plugins/
│   │       ├── swagger.ts
│   │       └── cors.ts
│   ├── package.json
│   ├── tsconfig.json
│   ├── .env.example
│   └── .env (create manually with API key)
├── frontend/
│   ├── src/
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── components/ui/
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   └── tailwind.config.js
└── .gitignore
```

## Plugin Pattern (Important)

Plugins must be **called as functions**, not registered with `fastify.register()`. See `@context/decisions/001-tech-stack.md` for details.

**plugins/cors.ts**:
```ts
import { FastifyInstance } from 'fastify';
import cors from '@fastify/cors';

export default async function corsPlugin(fastify: FastifyInstance) {
  await fastify.register(cors, { origin: "*" });
}
```

**app.ts** - Call plugins as functions:
```ts
import corsPlugin from './plugins/cors';
import swaggerPlugin from './plugins/swagger';

// ✅ Correct: call as function
await swaggerPlugin(fastify);
await corsPlugin(fastify);

// ❌ Wrong: do NOT use fastify.register(corsPlugin)
```

## Definition of Done
- [ ] Backend structure created with Fastify + Swagger
- [ ] Frontend structure created with Vite + React + TypeScript
- [ ] shadcn-ui initialized with button, card, input components
- [ ] Environment variables template created
- [ ] `pnpm install` runs successfully in both directories
- [ ] `pnpm run dev` starts both servers without errors

## After Completion
Run: `pnpm run dev` in both `backend/` and `frontend/` to verify setup works.

Then proceed to: **@context/agents/agent-backend.md**

