# Agent: Frontend - Todo App

## Purpose
Implement the React frontend with authentication and todo management features.

## Context Files to Load
- @context/intent/project-intent.md
- @context/intent/feature-user-auth.md
- @context/intent/feature-todo-crud.md
- @context/decisions/001-tech-stack.md
- @context/knowledge/patterns/api-design.md

## Scope
- **Allowed:** `frontend/src/`
- **Prohibited:** Modify backend code

## Execution Steps

1. **Create API Service**
   - Create `frontend/src/services/api.ts`
   - Configure Axios instance
   - Set base URL to backend
   - Handle credentials (cookies)

2. **Create Auth Context**
   - Create `frontend/src/context/AuthContext.tsx`
   - Manage user state
   - Provide: user, login, logout, signup, isAuthenticated
   - Persist auth state

3. **Create Auth Components**
   - Create `frontend/src/components/auth/LoginForm.tsx`
   - Create `frontend/src/components/auth/SignupForm.tsx`
   - Form validation
   - Error handling

4. **Create Todo Components**
   - Create `frontend/src/components/todos/TodoList.tsx`
   - Create `frontend/src/components/todos/TodoItem.tsx`
   - Create `frontend/src/components/todos/TodoForm.tsx`
   - Create `frontend/src/components/todos/TodoActions.tsx`

5. **Create Pages**
   - Create `frontend/src/pages/Home.tsx`
   - Create `frontend/src/pages/Login.tsx`
   - Create `frontend/src/pages/Signup.tsx`
   - Create `frontend/src/pages/Todos.tsx`

6. **Configure Routing**
   - Setup React Router
   - Protected routes for /todos
   - Redirect if not authenticated

7. **Create Layout**
   - Create `frontend/src/components/layout/Header.tsx`
   - Create `frontend/src/components/layout/Layout.tsx`
   - Navigation with auth status

## Expected Structure

```
frontend/src/
├── components/
│   ├── auth/
│   │   ├── LoginForm.tsx
│   │   └── SignupForm.tsx
│   ├── todos/
│   │   ├── TodoList.tsx
│   │   ├── TodoItem.tsx
│   │   ├── TodoForm.tsx
│   │   └── TodoActions.tsx
│   └── layout/
│       ├── Header.tsx
│       └── Layout.tsx
├── context/
│   └── AuthContext.tsx
├── pages/
│   ├── Home.tsx
│   ├── Login.tsx
│   ├── Signup.tsx
│   └── Todos.tsx
├── services/
│   └── api.ts
├── types/
│   ├── auth.ts
│   └── todo.ts
├── App.tsx
└── main.tsx
```

## Definition of Done
- [ ] API service configured with Axios
- [ ] Auth context manages user state
- [ ] Login/Signup forms work
- [ ] Protected routes redirect to login
- [ ] Todo list displays user's todos
- [ ] Can create, edit, toggle, delete todos
- [ ] Responsive design
- [ ] Error states handled

## Verification
```bash
cd frontend && pnpm run dev

# Test in browser
open http://localhost:5173

# Test flow:
# 1. Signup new user
# 2. Login
# 3. Create todo
# 4. Toggle complete
# 5. Edit todo
# 6. Delete todo
# 7. Logout
```

## After Completion
Proceed to: **@context/agents/agent-testing.md** (Optional)

