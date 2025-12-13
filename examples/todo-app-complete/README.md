# Complete Example: Todo App with Context Mesh

This is a **complete end-to-end example** demonstrating how to use Context Mesh in a real project. This example shows the full workflow from Intent to Build to Learn.

## 📋 Overview

**Project**: Simple Todo Application  
**Tech Stack**: React + TypeScript + Node.js + PostgreSQL  
**Duration**: Complete workflow demonstration

## 🎯 What You'll Learn

- How to structure Context Mesh for a real project
- How to create intent documents (project, features, bugs)
- How to document decisions during development
- How to update context in the Learn phase
- How to handle the complete workflow cycle

## 📁 Project Structure

```
todo-app-complete/
├── README.md                    # This file
├── AGENTS.md                    # Router for AI agents (references Context Mesh)
├── context/                     # Context Mesh structure
│   ├── intent/
│   │   ├── project-intent.md   # Overall project intent
│   │   ├── feature-user-auth.md # Feature: User authentication
│   │   ├── feature-todo-crud.md # Feature: Todo CRUD operations
│   │   └── bug-todo-persistence.md # Bug: Todo persistence issue
│   ├── decisions/
│   │   ├── 001-tech-stack.md    # Decision: Technology stack
│   │   ├── 002-auth-approach.md # Decision: Authentication approach
│   │   └── 003-database-schema.md # Decision: Database schema
│   ├── knowledge/
│   │   ├── patterns/
│   │   │   └── api-design.md   # Pattern: API design
│   │   └── anti-patterns/
│   │       └── avoid-direct-db.md # Anti-pattern: Direct DB access
│   └── evolution/
│       ├── changelog.md         # Project changelog
│       └── learning-001-auth.md # Learning: Authentication insights
└── code/                        # Generated code (example structure)
    ├── frontend/
    ├── backend/
    └── database/
```

## 🚀 Workflow Demonstration

This example demonstrates the complete Context Mesh workflow:

### Phase 1: Intent (Planning)

1. **Project Intent** → `context/intent/project-intent.md`
2. **Feature Intents** → `context/intent/feature-*.md`
3. **Technical Decisions** → `context/decisions/001-*.md`

### Phase 2: Build (Construction)

1. **AI generates code** based on context
2. **Decisions documented** as implementation progresses
3. **Context updated** with implementation details

### Phase 3: Learn (Learning)

1. **Context updated** to reflect actual code
2. **Learnings documented** → `context/evolution/learning-*.md`
3. **Decisions updated** with outcomes
4. **Intent refined** based on learnings

## 🤖 Building with AI Agents (Cursor/Copilot)

This example is designed to be built using AI agents like Cursor or GitHub Copilot. The context provided is sufficient for an AI agent to generate the complete application.

### About AGENTS.md

**Important**: Before starting, check if your project already has an `AGENTS.md` file:

- **If your project already has AGENTS.md:**
  - ✅ Use the existing `AGENTS.md` file
  - ✅ Update it to reference Context Mesh files if needed
  - ✅ Ensure it includes a "Context Files to Load" section pointing to your `context/` directory

- **If your project doesn't have AGENTS.md:**
  - ✅ Follow the example: [AGENTS.md.example](../../AGENTS.md.example)
  - ✅ Copy and adapt it to your project needs
  - ✅ Include all relevant Context Mesh file references
  - ✅ Keep it succinct - it should route to Context Mesh, not duplicate it

**This example includes an `AGENTS.md` file** that demonstrates how to integrate AGENTS.md with Context Mesh. You can use it as a reference or adapt it to your own project.

**Recommended**: Use `AGENTS.md` as the entry point. It acts as a router that references all Context Mesh files automatically.

### Step 1: Load Context into AI Agent

**Option A: Using AGENTS.md (Recommended)**
- Open Cursor/Copilot Chat
- Load `AGENTS.md` - it automatically references all Context Mesh files
- AI agents will load the relevant context files automatically

**Option B: Direct Context Loading**

**In Cursor:**
1. Open Cursor Chat (`Cmd/Ctrl + L` or click the chat icon)
2. Click "Attach Files" or drag and drop the entire `context/` folder
3. Or reference specific files: `@context/intent/project-intent.md`

**In GitHub Copilot Chat:**
1. Open Copilot Chat (View → Copilot Chat)
2. Reference files using: `# context/intent/project-intent.md`
3. Load multiple files by referencing them in sequence

**Recommended Context Loading Order:**
1. `@context/intent/project-intent.md` - Overall project goals
2. `@context/decisions/001-tech-stack.md` - Technology choices
3. `@context/decisions/004-dev-environment.md` - Development environment setup
4. `@context/decisions/002-auth-approach.md` - Authentication approach
5. `@context/decisions/003-database-schema.md` - Database design
6. `@context/intent/feature-user-auth.md` - Auth feature requirements
7. `@context/intent/feature-todo-crud.md` - Todo CRUD requirements
8. `@context/knowledge/patterns/api-design.md` - API patterns
9. `@context/knowledge/patterns/docker-compose.md` - Docker Compose setup
10. `@context/knowledge/anti-patterns/avoid-direct-db.md` - What to avoid
11. `@context/decisions/005-testing-strategy.md` - Testing approach
12. `@context/intent/feature-testing.md` - Testing requirements
13. `@context/decisions/006-ci-cd-pipeline.md` - CI/CD configuration
14. `@context/intent/feature-ci-cd.md` - CI/CD requirements
15. `@context/decisions/007-deployment-platforms.md` - Deployment platforms

### Step 2: Use These Prompts

> **💡 Context Mesh Philosophy**: Since context is the primary artifact, prompts should be **simple and reference the context**. The context files contain all the details (tech stack, patterns, anti-patterns, requirements).
> 
> **Approach Hierarchy:**
> 1. **✅ Simple Prompts** (Recommended - Default) - Start here
> 2. **✅ AI Agents (agent-*.md)** (Advanced) - When you need structured/reusable execution
> 3. **⚠️ Detailed Prompts** (Avoid) - Only for temporary tests
> 
> See [FRAMEWORK.md](../../FRAMEWORK.md) for complete guidance on choosing the right approach.

**Initial Setup Prompt:**
```
Create the project structure following @context/decisions/001-tech-stack.md
and @context/decisions/003-database-schema.md
```

**Build Authentication Prompt:**
```
Implement authentication following @context/intent/feature-user-auth.md
and @context/decisions/002-auth-approach.md
```

**Build Todo CRUD Prompt:**
```
Implement Todo CRUD following @context/intent/feature-todo-crud.md
```

**Build Frontend Integration Prompt:**
```
Create frontend following @context/knowledge/patterns/api-design.md
and integrate with the backend API
```

**Why Simple Prompts?**

- ✅ **Context is primary**: All details are in context files
- ✅ **Single source of truth**: Changes in context automatically reflect
- ✅ **Less maintenance**: Update context, not prompts
- ✅ **More reliable**: AI reads complete context, not just prompt summary
- ✅ **Aligned with Context Mesh philosophy**: Context drives code generation

**When to Use Detailed Prompts:**

You can create more detailed prompts if:
- You need specific execution instructions not in context
- You're testing a specific approach
- You want to override context temporarily
- You're learning and want explicit steps

But remember: **the recommendation is to put details in context, not prompts**.

### Step 3: Verify Against Context

After each generation, verify the code:
- ✅ Follows decisions from `context/decisions/`
- ✅ Matches patterns from `context/knowledge/patterns/`
- ✅ Avoids anti-patterns from `context/knowledge/anti-patterns/`
- ✅ Meets success criteria from `context/intent/`
- ✅ Uses service layer pattern (not direct DB access in routes)

---

## 📁 Complete Project Structure

After building, your project should have this structure:

```
todo-app/
├── context/                    # Context Mesh (already exists)
│   ├── intent/
│   ├── decisions/
│   ├── knowledge/
│   └── evolution/
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   │   ├── auth.routes.ts
│   │   │   └── todos.routes.ts
│   │   ├── services/
│   │   │   ├── auth.service.ts
│   │   │   └── todo.service.ts
│   │   ├── middleware/
│   │   │   ├── auth.middleware.ts
│   │   │   └── error.middleware.ts
│   │   ├── dto/
│   │   │   ├── auth.dto.ts
│   │   │   └── todo.dto.ts
│   │   └── app.ts
│   ├── prisma/
│   │   ├── schema.prisma
│   │   └── migrations/
│   ├── .env
│   ├── .env.example
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── auth/
│   │   │   │   ├── Login.tsx
│   │   │   │   ├── Signup.tsx
│   │   │   │   └── Logout.tsx
│   │   │   └── todos/
│   │   │       ├── TodoList.tsx
│   │   │       ├── TodoItem.tsx
│   │   │       └── TodoForm.tsx
│   │   ├── pages/
│   │   │   ├── Home.tsx
│   │   │   └── Todos.tsx
│   │   ├── services/
│   │   │   └── api.ts
│   │   ├── context/
│   │   │   └── AuthContext.tsx
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── .env
│   ├── .env.example
│   ├── package.json
│   ├── tsconfig.json
│   └── vite.config.ts
└── README.md
```

---

## 🚀 Quick Start: Build This App

### Prerequisites

Before starting, ensure you have the following installed and configured:

**Required**:
- [ ] **Node.js 18+** installed (`node --version`)
- [ ] **npm** or **yarn** (comes with Node.js)
- [ ] **Docker** and **Docker Compose** installed (`docker --version`, `docker-compose --version`)
- [ ] **Git** installed (`git --version`)
- [ ] **Cursor IDE** or **GitHub Copilot** enabled

**Optional (for CI/CD testing)**:
- [ ] **act** (for testing GitHub Actions locally) - See [Testing CI/CD Locally](#testing-cicd-locally)

**Note**: You don't need to install PostgreSQL locally - we use Docker Compose for the database. See [Development Environment Setup](#development-environment-setup) for details.

### Step-by-Step Build Process

#### 1. Setup Project Directory

```bash
# Create project directory
mkdir todo-app
cd todo-app

# Copy the context folder from this example
cp -r /path/to/examples/todo-app-complete/context ./
```

#### 2. Load Context in AI Agent

**Option A: Using AGENTS.md (Recommended)**
- Open Cursor/Copilot Chat
- Load `AGENTS.md` - it automatically references all Context Mesh files
- AI agents will load the relevant context files automatically

**Option B: Direct Context Loading**
- **In Cursor**: Open Cursor Chat (`Cmd/Ctrl + L`), attach the `context/` folder
- **In GitHub Copilot**: Open Copilot Chat, reference `# context/intent/project-intent.md`

**Note**: `AGENTS.md` acts as a router that references Context Mesh files. It's the recommended approach.

#### 3. Generate Project Structure

Use this simple prompt in your AI agent:
```
Create the project structure following @context/decisions/001-tech-stack.md
and @context/decisions/003-database-schema.md
```

The context files contain all the details - tech stack, database schema, etc.

#### 4. Setup Development Environment

**Start PostgreSQL with Docker Compose**:
```bash
# From project root
docker-compose up -d
```

This starts PostgreSQL in a Docker container. The database will be available at `localhost:5432`.

**Verify database is running**:
```bash
docker-compose ps
# Should show postgres container running
```

See [Development Environment Setup](#development-environment-setup) for more details.

#### 5. Setup Backend

After AI generates the structure, run:
```bash
cd backend
npm install

# Create .env file (copy from .env.example if provided)
# DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp

npx prisma migrate dev --name init
npx prisma generate
```

#### 6. Build Authentication

Use this simple prompt:
```
Implement authentication following @context/intent/feature-user-auth.md
and @context/decisions/002-auth-approach.md
```

The context files contain all requirements, success criteria, and technical approach.

#### 7. Build Todo CRUD

Use this simple prompt:
```
Implement Todo CRUD following @context/intent/feature-todo-crud.md
```

The context file contains all requirements, success criteria, and security needs.

#### 8. Build Frontend

Use this simple prompt:
```
Create frontend following @context/knowledge/patterns/api-design.md
and integrate with the backend API
```

The API pattern file contains all endpoint structures, request/response formats, and error handling.

#### 9. Implement Testing

Use this simple prompt:
```
Implement unit tests following @context/intent/feature-testing.md
and @context/decisions/005-testing-strategy.md
```

The context files contain all testing requirements, patterns, and examples.

#### 10. Setup CI/CD

Use this simple prompt:
```
Create GitHub Actions workflows following @context/intent/feature-ci-cd.md
and @context/decisions/006-ci-cd-pipeline.md
```

The context files contain complete workflow configurations for backend and frontend.

#### 11. Test the Application Locally

```bash
# Start backend
cd backend
npm run dev

# Start frontend (in another terminal)
cd frontend
npm run dev
```

---

## 🐳 Development Environment Setup

### Docker Compose for PostgreSQL

The project uses Docker Compose to run PostgreSQL locally. This avoids the need to install PostgreSQL on your machine.

**Start Database**:
```bash
docker-compose up -d
```

**Stop Database**:
```bash
docker-compose down
```

**View Logs**:
```bash
docker-compose logs -f postgres
```

**Reset Database** (removes all data):
```bash
docker-compose down -v
docker-compose up -d
```

**Connection String**:
```
DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp
```

See `@context/decisions/004-dev-environment.md` and `@context/knowledge/patterns/docker-compose.md` for complete details.

---

## 🧪 Testing

### Running Tests

**Backend**:
```bash
cd backend
npm test              # Run tests in watch mode
npm test -- --coverage  # Run tests with coverage report
```

**Frontend**:
```bash
cd frontend
npm test              # Run tests in watch mode
npm test -- --coverage  # Run tests with coverage report
```

### Test Coverage

The project requires **minimum 70% code coverage** for:
- Branches
- Functions
- Lines
- Statements

See `@context/decisions/005-testing-strategy.md` and `@context/knowledge/patterns/testing.md` for testing patterns and examples.

---

## 🚀 CI/CD Pipeline

### GitHub Actions Workflows

The project includes GitHub Actions workflows for:
- **Backend**: `.github/workflows/backend.yml` - Tests, lints, and deploys to Railway
- **Frontend**: `.github/workflows/frontend.yml` - Tests, lints, builds, and deploys to Vercel

### Testing CI/CD Locally

You can test GitHub Actions workflows locally using `act`:

**Install act**:
```bash
# macOS
brew install act

# Linux
curl https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash

# Windows (via Chocolatey)
choco install act-cli
```

**Run Workflow Locally**:
```bash
# Test backend workflow
act -W .github/workflows/backend.yml

# Test frontend workflow
act -W .github/workflows/frontend.yml

# Run specific job
act -j test -W .github/workflows/backend.yml

# Use secrets (if needed)
act -W .github/workflows/backend.yml --secret RAILWAY_TOKEN=your_token
```

**Limitations**:
- Deployment steps may not work locally (require actual services)
- Some actions may not be compatible with `act`
- Use for syntax validation and basic testing

**What You Need to Test CI/CD**:
- GitHub repository (public or private)
- GitHub Actions enabled (automatic for public repos)
- Secrets configured in GitHub (for deployment):
  - `RAILWAY_TOKEN` (backend deployment)
  - `VERCEL_TOKEN`, `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID` (frontend deployment)
  - `VITE_API_URL` (frontend build)

See `@context/decisions/006-ci-cd-pipeline.md` and `@context/knowledge/patterns/github-actions.md` for complete details.

---

## 🌐 Deployment

### Railway (Backend)

**Setup**:
1. Create account at https://railway.app
2. Sign up with GitHub
3. Create new project → Deploy from GitHub repo
4. Select repository and `backend` directory
5. Add PostgreSQL database (Railway → New → Database → PostgreSQL)
6. Set environment variables in Railway dashboard:
   - `NODE_ENV=production`
   - `JWT_SECRET=<generate-secure-secret>`
   - `JWT_EXPIRES_IN=7d`
   - `DATABASE_URL` (auto-set by Railway)

**Deployment**:
- Automatic on push to `main` branch (via GitHub Actions)
- Or manual: Railway dashboard → Deploy

### Vercel (Frontend)

**Setup**:
1. Create account at https://vercel.com
2. Sign up with GitHub
3. Import repository
4. Configure:
   - Root directory: `frontend`
   - Framework preset: Vite
   - Build command: `npm run build`
   - Output directory: `dist`
5. Set environment variables:
   - `VITE_API_URL=https://your-backend.railway.app/api/v1`

**Deployment**:
- Automatic on push to `main` branch (via GitHub Actions)
- Preview deployments for PRs
- Production URL: `https://your-project.vercel.app`

### Required Secrets for CI/CD

Configure these in GitHub repository settings (Settings → Secrets and variables → Actions):

**Backend**:
- `RAILWAY_TOKEN`: Get from Railway dashboard → Account → Tokens

**Frontend**:
- `VERCEL_TOKEN`: Get from Vercel dashboard → Settings → Tokens
- `VERCEL_ORG_ID`: Get from Vercel dashboard → Settings → General
- `VERCEL_PROJECT_ID`: Get from Vercel project settings
- `VITE_API_URL`: Your Railway backend URL (e.g., `https://your-backend.railway.app/api/v1`)

See `@context/decisions/007-deployment-platforms.md` for complete deployment guide.

---

## 📖 How to Use This Example

### For Learning Context Mesh

1. **Read the files in order**:
   - Start with `context/intent/project-intent.md`
   - Then read feature intents
   - Review decisions
   - Check learnings

2. **Follow the workflow**:
   - See how Intent → Build → Learn flows
   - Notice how context evolves
   - Observe decision documentation

3. **Adapt to your project**:
   - Use as a template
   - Modify structure as needed
   - Keep it simple

### For Building the App

Follow the "Building with AI Agents" section above to actually build the application using the context provided.

## 🎓 Key Takeaways

- **Intent drives everything**: Clear intent makes Build faster
- **Decisions in Intent phase**: Planning decisions early speeds up Build
- **Context evolves**: Update context continuously, not just at the end
- **Learnings feed back**: Learnings refine intent for next iteration

## 📚 Related Documentation

- [FRAMEWORK.md](../../FRAMEWORK.md) - Complete framework structure
- [GETTING_STARTED.md](../../GETTING_STARTED.md) - Getting started guide
- [EXAMPLES.md](../../EXAMPLES.md) - More examples

---

**Note**: This is a demonstration example. In a real project, you would have actual code files. The structure and workflow shown here are what you would follow in your own projects.

