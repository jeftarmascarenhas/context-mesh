# Agent: Setup - Todo App

## Purpose
Initialize the project structure with backend (Express + TypeScript) and frontend (Vite + React + TypeScript).

## Context Files to Load
- @context/intent/project-intent.md
- @context/decisions/001-tech-stack.md

## Scope
- **Allowed:** Root project, `backend/`, `frontend/`
- **Prohibited:** Don't implement features, don't setup database

## Execution Steps

1. **Create Backend Structure**
   - Initialize Node.js project with TypeScript
   - Configure Express with basic middleware
   - Create directory structure (routes, services, middleware, dto)
   - Setup Prisma (schema will be created in database phase)
   - Create `.env.example`

2. **Create Frontend Structure**
   - Initialize Vite + React + TypeScript project
   - Configure Tailwind CSS
   - Setup React Router
   - Create base directory structure (components, pages, services, context)
   - Create `.env.example`

3. **Create Root Files**
   - Create `.gitignore`

## Expected Output

```
todo-app/
├── backend/
│   ├── src/
│   │   ├── app.ts
│   │   ├── middleware/
│   │   ├── routes/
│   │   ├── services/
│   │   └── dto/
│   ├── prisma/
│   ├── package.json
│   ├── tsconfig.json
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── context/
│   ├── package.json
│   ├── tsconfig.json
│   └── vite.config.ts
└── .gitignore
```

## Environment Variables

**backend/.env.example**
```
DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp
JWT_SECRET=your-secret-key-here
JWT_EXPIRES_IN=7d
PORT=3000
NODE_ENV=development
```

**frontend/.env.example**
```
VITE_API_URL=http://localhost:3000/api/v1
```

## Definition of Done
- [ ] Backend structure created with Express + TypeScript
- [ ] Frontend structure created with Vite + React + TypeScript
- [ ] Directory structure organized
- [ ] Environment variables template created
- [ ] `pnpm install` runs in both directories
- [ ] TypeScript compiles without errors

## Verification
```bash
# Backend
cd backend
pnpm install
pnpm run build  # Should compile without errors

# Frontend
cd frontend
pnpm install
pnpm run build  # Should compile without errors
```

## After Completion
Proceed to: **@context/agents/agent-database.md**
