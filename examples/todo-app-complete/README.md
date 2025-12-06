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

### Step 1: Load Context into AI Agent

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
3. `@context/decisions/002-auth-approach.md` - Authentication approach
4. `@context/decisions/003-database-schema.md` - Database design
5. `@context/intent/feature-user-auth.md` - Auth feature requirements
6. `@context/intent/feature-todo-crud.md` - Todo CRUD requirements
7. `@context/knowledge/patterns/api-design.md` - API patterns
8. `@context/knowledge/anti-patterns/avoid-direct-db.md` - What to avoid

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
- Node.js 18+ installed
- PostgreSQL installed and running
- Cursor IDE or GitHub Copilot enabled
- Git (optional, for version control)

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

**In Cursor:**
- Open Cursor Chat (`Cmd/Ctrl + L`)
- Attach the `context/` folder
- Or use: `@context/intent/project-intent.md`

**In GitHub Copilot:**
- Open Copilot Chat
- Reference: `# context/intent/project-intent.md`

#### 3. Generate Project Structure

Use this simple prompt in your AI agent:
```
Create the project structure following @context/decisions/001-tech-stack.md
and @context/decisions/003-database-schema.md
```

The context files contain all the details - tech stack, database schema, etc.

#### 4. Setup Backend

After AI generates the structure, run:
```bash
cd backend
npm install
npx prisma migrate dev --name init
npx prisma generate
```

#### 5. Build Authentication

Use this simple prompt:
```
Implement authentication following @context/intent/feature-user-auth.md
and @context/decisions/002-auth-approach.md
```

The context files contain all requirements, success criteria, and technical approach.

#### 6. Build Todo CRUD

Use this simple prompt:
```
Implement Todo CRUD following @context/intent/feature-todo-crud.md
```

The context file contains all requirements, success criteria, and security needs.

#### 7. Build Frontend

Use this simple prompt:
```
Create frontend following @context/knowledge/patterns/api-design.md
and integrate with the backend API
```

The API pattern file contains all endpoint structures, request/response formats, and error handling.

#### 8. Test the Application

```bash
# Start backend
cd backend
npm run dev

# Start frontend (in another terminal)
cd frontend
npm run dev
```

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

