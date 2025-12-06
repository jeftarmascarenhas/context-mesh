# Testing Guide: Todo App Example

This guide will help you test if the Todo App example is functional by following the README instructions.

## 🎯 Test Objective

Verify that:
1. The context provided is sufficient for an AI agent to generate a working Todo application
2. The README instructions are clear and actionable
3. The generated application works end-to-end

## 📋 Prerequisites Checklist

Before starting, ensure you have:
- [ ] Node.js 18+ installed (`node --version`)
- [ ] PostgreSQL installed and running (`psql --version`)
- [ ] Cursor IDE or GitHub Copilot enabled
- [ ] Git installed (optional)
- [ ] Terminal/Command line access

## 🧪 Test Plan

### Phase 1: Context Validation

**Objective**: Verify that all necessary context files exist and are complete.

**Steps**:
1. Navigate to the example directory:
   ```bash
   cd examples/todo-app-complete
   ```

2. Verify context structure exists:
   ```bash
   ls -la context/
   ls -la context/intent/
   ls -la context/decisions/
   ls -la context/knowledge/
   ls -la context/evolution/
   ```

3. Check that all required files exist:
   - [ ] `context/intent/project-intent.md` - Project overview
   - [ ] `context/intent/feature-user-auth.md` - Auth requirements
   - [ ] `context/intent/feature-todo-crud.md` - CRUD requirements
   - [ ] `context/decisions/001-tech-stack.md` - Tech stack
   - [ ] `context/decisions/002-auth-approach.md` - Auth approach
   - [ ] `context/decisions/003-database-schema.md` - Database schema
   - [ ] `context/knowledge/patterns/api-design.md` - API pattern
   - [ ] `context/knowledge/anti-patterns/avoid-direct-db.md` - Anti-pattern

4. Read each file and verify:
   - [ ] Project intent is clear and complete
   - [ ] Feature intents have success criteria
   - [ ] Decisions include rationale and alternatives
   - [ ] Database schema is complete (Prisma format)
   - [ ] API pattern shows request/response format
   - [ ] Anti-pattern shows what to avoid

**Expected Result**: All context files exist and contain sufficient information for code generation.

---

### Phase 2: README Instructions Test

**Objective**: Verify that README instructions are clear and actionable.

**Steps**:
1. Read the README.md file completely
2. Check that it includes:
   - [ ] Section "Building with AI Agents"
   - [ ] Step-by-step instructions for loading context
   - [ ] Specific prompts to use with AI agents
   - [ ] Complete project structure
   - [ ] Prerequisites list
   - [ ] Quick start guide

3. Verify prompts are:
   - [ ] Clear and specific
   - [ ] Reference context files correctly
   - [ ] Include all necessary steps
   - [ ] Follow Context Mesh patterns

**Expected Result**: README provides clear, actionable instructions for building the app.

---

### Phase 3: AI Agent Context Loading Test

**Objective**: Test if context can be loaded into AI agents (Cursor/Copilot).

**Steps**:

#### Test with Cursor:
1. Open Cursor IDE
2. Open the `examples/todo-app-complete` folder
3. Open Cursor Chat (`Cmd/Ctrl + L`)
4. Try to attach context files:
   - [ ] Attach entire `context/` folder
   - [ ] Reference specific file: `@context/intent/project-intent.md`
   - [ ] Verify AI can read the files

5. Test context understanding:
   ```
   What is this project about? Read @context/intent/project-intent.md
   ```
   - [ ] AI correctly identifies it's a Todo app
   - [ ] AI understands the tech stack
   - [ ] AI understands the requirements

#### Test with GitHub Copilot:
1. Open VS Code with Copilot enabled
2. Open the `examples/todo-app-complete` folder
3. Open Copilot Chat
4. Reference context files:
   ```
   # context/intent/project-intent.md
   What is this project about?
   ```
   - [ ] Copilot can read the file
   - [ ] Copilot understands the context

**Expected Result**: AI agents can successfully load and understand the context files.

---

### Phase 4: Code Generation Test

**Objective**: Test if AI can generate code using the provided context.

**Steps**:

1. **Create a new project directory**:
   ```bash
   mkdir ~/test-todo-app
   cd ~/test-todo-app
   cp -r /path/to/examples/todo-app-complete/context ./
   ```

2. **Load context in AI agent** (follow README instructions)

3. **Test Initial Setup Prompt**:
   Use the prompt from README:
   ```
   Using the context from @context/, create the initial project structure for a Todo application:
   1. Create backend/ folder with Express + TypeScript + Prisma setup
   2. Create frontend/ folder with React + TypeScript + Vite setup
   3. Follow the tech stack decision in @context/decisions/001-tech-stack.md
   4. Use the database schema from @context/decisions/003-database-schema.md
   5. Create package.json files with all necessary dependencies
   6. Create tsconfig.json files for both frontend and backend
   7. Create Prisma schema file based on the schema in the decision document
   8. Create .env.example files with required environment variables
   ```

   Verify generated:
   - [ ] `backend/` folder exists
   - [ ] `frontend/` folder exists
   - [ ] `backend/package.json` with correct dependencies
   - [ ] `frontend/package.json` with correct dependencies
   - [ ] `backend/tsconfig.json`
   - [ ] `frontend/tsconfig.json`
   - [ ] `backend/prisma/schema.prisma` with User and Todo models
   - [ ] `.env.example` files

4. **Test Authentication Prompt**:
   Use the prompt from README and verify:
   - [ ] Auth service layer created (not direct DB access)
   - [ ] Auth routes created
   - [ ] JWT middleware created
   - [ ] DTOs with validation created
   - [ ] React auth components created

5. **Test Todo CRUD Prompt**:
   Use the prompt from README and verify:
   - [ ] Todo service layer created
   - [ ] Todo routes created
   - [ ] User filtering implemented
   - [ ] React Todo components created

**Expected Result**: AI generates code that follows the context and patterns.

---

### Phase 5: Application Functionality Test

**Objective**: Verify the generated application works end-to-end.

**Steps**:

1. **Setup Backend**:
   ```bash
   cd backend
   npm install
   ```

2. **Setup Database**:
   ```bash
   # Create .env file with DATABASE_URL
   echo "DATABASE_URL=postgresql://user:password@localhost:5432/todoapp" > .env
   
   # Run migrations
   npx prisma migrate dev --name init
   npx prisma generate
   ```

3. **Start Backend**:
   ```bash
   npm run dev
   ```
   - [ ] Backend starts without errors
   - [ ] Server listens on expected port (e.g., 3000)
   - [ ] No TypeScript errors

4. **Test Backend API** (using curl or Postman):
   
   **Test Signup**:
   ```bash
   curl -X POST http://localhost:3000/api/v1/auth/signup \
     -H "Content-Type: application/json" \
     -d '{"email":"test@example.com","password":"password123","name":"Test User"}'
   ```
   - [ ] Returns 201 with user data
   - [ ] Password is hashed (not plain text)
   - [ ] JWT token returned

   **Test Login**:
   ```bash
   curl -X POST http://localhost:3000/api/v1/auth/login \
     -H "Content-Type: application/json" \
     -d '{"email":"test@example.com","password":"password123"}'
   ```
   - [ ] Returns 200 with JWT token
   - [ ] Token is valid

   **Test Create Todo** (with JWT):
   ```bash
   curl -X POST http://localhost:3000/api/v1/todos \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer YOUR_JWT_TOKEN" \
     -d '{"title":"Test Todo","description":"Test description","category":"Test"}'
   ```
   - [ ] Returns 201 with todo data
   - [ ] Todo is associated with user
   - [ ] Follows API pattern format

   **Test Get Todos**:
   ```bash
   curl -X GET http://localhost:3000/api/v1/todos \
     -H "Authorization: Bearer YOUR_JWT_TOKEN"
   ```
   - [ ] Returns 200 with todos array
   - [ ] Only returns todos for authenticated user
   - [ ] Follows API pattern format

5. **Setup Frontend**:
   ```bash
   cd ../frontend
   npm install
   ```

6. **Start Frontend**:
   ```bash
   npm run dev
   ```
   - [ ] Frontend starts without errors
   - [ ] Opens in browser (e.g., http://localhost:5173)
   - [ ] No TypeScript errors

7. **Test Frontend Functionality**:
   - [ ] Can navigate to signup page
   - [ ] Can create account
   - [ ] Can login
   - [ ] Can see todos page (protected route)
   - [ ] Can create todo
   - [ ] Can view todos list
   - [ ] Can update todo
   - [ ] Can delete todo
   - [ ] Can mark todo as complete/incomplete
   - [ ] Can logout
   - [ ] Unauthenticated users redirected to login

**Expected Result**: Application works end-to-end with all features functional.

---

### Phase 6: Context Compliance Test

**Objective**: Verify generated code follows Context Mesh patterns and decisions.

**Steps**:

1. **Check Tech Stack Compliance**:
   - [ ] Uses React 18+ with TypeScript
   - [ ] Uses Vite for frontend build
   - [ ] Uses Express with TypeScript
   - [ ] Uses Prisma ORM
   - [ ] Uses PostgreSQL
   - [ ] Uses JWT for authentication

2. **Check Architecture Compliance**:
   - [ ] Uses service layer (not direct DB access in routes)
   - [ ] Follows API pattern from `context/knowledge/patterns/api-design.md`
   - [ ] Avoids anti-pattern from `context/knowledge/anti-patterns/avoid-direct-db.md`
   - [ ] Uses DTOs with validation
   - [ ] Implements error handling middleware

3. **Check Feature Compliance**:
   - [ ] Auth follows `context/intent/feature-user-auth.md` success criteria
   - [ ] Todo CRUD follows `context/intent/feature-todo-crud.md` success criteria
   - [ ] Database schema matches `context/decisions/003-database-schema.md`
   - [ ] Auth approach matches `context/decisions/002-auth-approach.md`

4. **Check Code Quality**:
   - [ ] TypeScript strict mode enabled
   - [ ] No `any` types (or minimal)
   - [ ] Proper error handling
   - [ ] Input validation
   - [ ] Security best practices (password hashing, JWT)

**Expected Result**: Generated code fully complies with Context Mesh decisions and patterns.

---

## ✅ Test Results Summary

After completing all phases, document:

### Context Validation
- [ ] All context files exist and are complete
- [ ] Context provides sufficient information

### README Quality
- [ ] Instructions are clear
- [ ] Prompts are actionable
- [ ] Structure is well-documented

### AI Agent Integration
- [ ] Context loads successfully
- [ ] AI understands the context
- [ ] Prompts work as expected

### Code Generation
- [ ] AI generates complete project structure
- [ ] Code follows context decisions
- [ ] Code follows patterns

### Application Functionality
- [ ] Backend works correctly
- [ ] Frontend works correctly
- [ ] All features functional
- [ ] Security implemented correctly

### Context Compliance
- [ ] Tech stack matches decisions
- [ ] Architecture follows patterns
- [ ] Features meet success criteria

---

## 🐛 Troubleshooting

### If context doesn't load:
- Check file paths are correct
- Verify AI agent has access to files
- Try referencing files individually

### If code generation fails:
- Verify all context files are loaded
- Check prompts reference correct files
- Try breaking prompts into smaller steps

### If application doesn't work:
- Check database connection
- Verify environment variables
- Check console for errors
- Verify all dependencies installed

### If code doesn't follow patterns:
- Re-read the pattern files
- Ask AI to regenerate specific parts
- Manually verify against context

---

## 📝 Notes

- This is a comprehensive test - it may take 2-4 hours to complete
- Some steps may require manual intervention
- The goal is to verify the example is functional, not perfect
- Document any issues or improvements needed

---

**Test Date**: _______________  
**Tester**: _______________  
**AI Agent Used**: _______________ (Cursor/Copilot/Other)  
**Result**: _______________ (Pass/Fail/Partial)

