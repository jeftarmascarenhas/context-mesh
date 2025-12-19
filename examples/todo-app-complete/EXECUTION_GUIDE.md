# Todo App Complete - Execution Guide

A complete Todo App demonstrating full Context Mesh workflow with testing, CI/CD, and deployment.

**Tech Stack**: React + TypeScript + Vite | Express + Prisma + PostgreSQL | Jest | GitHub Actions | Railway + Vercel

---

## Prerequisites

- Node.js 18+
- pnpm (or npm)
- Docker and Docker Compose
- Git
- Cursor IDE or GitHub Copilot
- GitHub account (for CI/CD)
- Railway account (optional, for deployment)
- Vercel account (optional, for deployment)

---

## How to Execute an Agent

When you see `Execute @context/agents/agent-*.md` in this guide, follow these steps:

1. **Open your AI assistant** (Cursor Chat, GitHub Copilot Chat, or similar)
2. **Type the command**: `Execute @context/agents/agent-setup.md` (replace with the agent name for each phase)
3. **Review the generated code** before accepting
4. **Run verification commands** after accepting the changes
5. **Check the Definition of Done (DoD)** to ensure everything is complete

**Note**: The `@context/` syntax works in Cursor. For other IDEs, you may need to:
- Use the full file path: `context/agents/agent-setup.md`
- Or copy the agent file content and paste it into your AI chat

---

## Execution Flow

```
1. Load Context
   ↓
2. Execute Agent 1: Setup
   → Verify → Approve
   ↓
3. Execute Agent 2: Database
   → Verify → Approve
   ↓
4. Execute Agent 3: Auth
   → Verify → Approve
   ↓
5. Execute Agent 4: Todo CRUD
   → Verify → Approve
   ↓
6. Execute Agent 5: Frontend
   → Verify → Approve
   ↓
7. Execute Agent 6: Testing (Optional)
   → Verify → Approve
   ↓
8. Execute Agent 7: CI/CD (Optional)
   → Verify → Approve
   ↓
9. Final Test
```

---

## Phase 1: Setup

### Execute Agent
```
Execute @context/agents/agent-setup.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-setup.md` for complete criteria.

**Quick reference:**
- [ ] Backend structure created (Express + TypeScript + Prisma)
- [ ] Frontend structure created (Vite + React + TypeScript)
- [ ] Docker Compose file created for PostgreSQL
- [ ] Environment variables template created
- [ ] `pnpm install` runs in both directories
- [ ] `pnpm run dev` starts both servers

### Verification
```bash
# Check structure
ls backend/src
ls frontend/src

# Test install
cd backend && pnpm install
cd ../frontend && pnpm install
```

✅ All DoD criteria met → Proceed to Phase 2

---

## Phase 2: Database

### Execute Agent
```
Execute @context/agents/agent-database.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-database.md` for complete criteria.

**Quick reference:**
- [ ] PostgreSQL running via Docker Compose
- [ ] Prisma schema created with User and Todo models
- [ ] Migrations run successfully
- [ ] Prisma client generated

### Verification
```bash
# Start database
docker-compose up -d

# Verify running
docker-compose ps

# Run migrations
cd backend
npx prisma migrate dev --name init
npx prisma generate

# Test connection
npx prisma studio
```

✅ All DoD criteria met → Proceed to Phase 3

---

## Phase 3: Authentication

### Execute Agent
```
Execute @context/agents/agent-auth.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-auth.md` for complete criteria.

**Quick reference:**
- [ ] Auth service implemented (signup, login, logout)
- [ ] JWT tokens with httpOnly cookies
- [ ] Auth middleware for protected routes
- [ ] Password hashing with bcrypt
- [ ] Auth routes created (/auth/signup, /auth/login, /auth/logout)

### Verification
```bash
cd backend && pnpm run dev

# Test signup
curl -X POST http://localhost:3000/api/v1/auth/signup \
  -H "Content-Type: application/json" \
  -d '{"email":"test@test.com","password":"password123","name":"Test"}'

# Test login
curl -X POST http://localhost:3000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@test.com","password":"password123"}'
```

✅ All DoD criteria met → Proceed to Phase 4

---

## Phase 4: Todo CRUD

### Execute Agent
```
Execute @context/agents/agent-todo.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-todo.md` for complete criteria.

**Quick reference:**
- [ ] Todo service implemented (create, read, update, delete)
- [ ] Todo routes created (GET, POST, PUT, DELETE /todos)
- [ ] Routes protected by auth middleware
- [ ] Todos scoped to authenticated user

### Verification
```bash
cd backend && pnpm run dev

# Login first to get token
# Then test CRUD operations

# Create todo
curl -X POST http://localhost:3000/api/v1/todos \
  -H "Content-Type: application/json" \
  -H "Cookie: token=YOUR_JWT_TOKEN" \
  -d '{"title":"Test todo","description":"Test description"}'

# Get todos
curl http://localhost:3000/api/v1/todos \
  -H "Cookie: token=YOUR_JWT_TOKEN"
```

✅ All DoD criteria met → Proceed to Phase 5

---

## Phase 5: Frontend

### Execute Agent
```
Execute @context/agents/agent-frontend.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-frontend.md` for complete criteria.

**Quick reference:**
- [ ] API client created
- [ ] Auth components (Login, Signup, Logout)
- [ ] Todo components (TodoList, TodoItem, TodoForm)
- [ ] Auth context for state management
- [ ] Protected routes
- [ ] Responsive design

### Verification
```bash
cd frontend && pnpm run dev

# Test
open http://localhost:5173

# Test scenarios:
# - Signup new user
# - Login
# - Create todo
# - Toggle todo complete
# - Delete todo
# - Logout
```

✅ All DoD criteria met → Proceed to Phase 6 (Optional)

---

## Phase 6: Testing (Optional)

### Execute Agent
```
Execute @context/agents/agent-testing.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-testing.md` for complete criteria.

**Quick reference:**
- [ ] Jest configured for backend
- [ ] React Testing Library configured for frontend
- [ ] Auth service tests created
- [ ] Todo service tests created
- [ ] Test coverage > 70%

### Verification
```bash
# Backend tests
cd backend && pnpm test -- --coverage

# Frontend tests
cd frontend && pnpm test -- --coverage
```

✅ All DoD criteria met → Proceed to Phase 7 (Optional)

---

## Phase 7: CI/CD (Optional)

### Execute Agent
```
Execute @context/agents/agent-cicd.md
```

### Definition of Done (DoD)
See **Definition of Done** section in `@context/agents/agent-cicd.md` for complete criteria.

**Quick reference:**
- [ ] Backend workflow created (.github/workflows/backend.yml)
- [ ] Frontend workflow created (.github/workflows/frontend.yml)
- [ ] Tests run on PR
- [ ] Deploy on push to main (if secrets configured)

### Verification
```bash
# Test locally with act (if installed)
act -W .github/workflows/backend.yml -j test

# Or push to GitHub and check Actions tab
```

✅ All DoD criteria met → Final Test

---

## Final Test

1. **Start all services**:
   ```bash
   # Terminal 1: Database
   docker-compose up -d
   
   # Terminal 2: Backend
   cd backend && pnpm run dev
   
   # Terminal 3: Frontend
   cd frontend && pnpm run dev
   ```

2. **Open** http://localhost:5173

3. **Test complete flow**:
   - [ ] Signup new user
   - [ ] Login
   - [ ] Create multiple todos
   - [ ] Toggle todo complete
   - [ ] Edit todo
   - [ ] Delete todo
   - [ ] Logout
   - [ ] Login again (data persists)

---

## Project Structure

```
todo-app-complete/
├── EXECUTION_GUIDE.md      # This file
├── AGENTS.md               # Router for AI agents
├── context/
│   ├── intent/
│   │   ├── project-intent.md
│   │   ├── feature-user-auth.md
│   │   ├── feature-todo-crud.md
│   │   ├── feature-testing.md
│   │   └── feature-ci-cd.md
│   ├── decisions/
│   │   ├── 001-tech-stack.md
│   │   ├── 002-auth-approach.md
│   │   ├── 003-database-schema.md
│   │   └── ...
│   ├── knowledge/
│   │   ├── patterns/
│   │   └── anti-patterns/
│   ├── agents/
│   │   ├── agent-setup.md
│   │   ├── agent-database.md
│   │   ├── agent-auth.md
│   │   ├── agent-todo.md
│   │   ├── agent-frontend.md
│   │   ├── agent-testing.md
│   │   └── agent-cicd.md
│   └── evolution/
│       └── changelog.md
├── backend/
│   ├── src/
│   └── prisma/
├── frontend/
│   └── src/
└── README.md
```

---

## Troubleshooting

### Database won't start
```bash
docker-compose down -v
docker-compose up -d
```

### Prisma errors
```bash
cd backend
npx prisma generate
npx prisma migrate reset
```

### Auth not working
- Check JWT_SECRET in .env
- Check cookies are being set (httpOnly)
- Check CORS configuration

### Frontend can't connect
- Verify backend is running on port 3000
- Check VITE_API_URL in frontend/.env

---

## Deployment (Optional)

### Railway (Backend)
1. Create Railway account
2. Connect GitHub repo
3. Select backend directory
4. Add PostgreSQL database
5. Set environment variables

### Vercel (Frontend)
1. Create Vercel account
2. Import GitHub repo
3. Select frontend directory
4. Set VITE_API_URL to Railway backend URL

---

## Learn More

- [Framework Documentation](../../FRAMEWORK.md)
- [Getting Started](../../GETTING_STARTED.md)
- [Minimal Example: Weather App](../weather-app-minimal/)

---

**Time**: 2-3 hours | **Complexity**: High

