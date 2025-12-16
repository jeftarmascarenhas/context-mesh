# Agent: Testing - Todo App

## Purpose
Implement unit tests for backend services and frontend components with Jest and React Testing Library.

## Context Files to Load
- @context/intent/feature-testing.md
- @context/decisions/005-testing-strategy.md
- @context/knowledge/patterns/testing.md

## Scope
- **Allowed:** `backend/src/`, `frontend/src/`, test config files
- **Prohibited:** Modify application logic

## Execution Steps

### Backend

1. **Configure Jest**
   - Add Jest and ts-jest dependencies
   - Create `jest.config.js`
   - Add test script to package.json

2. **Create Auth Service Tests**
   - Create `backend/src/services/__tests__/auth.service.test.ts`
   - Test: signup, login, password hashing
   - Mock Prisma client

3. **Create Todo Service Tests**
   - Create `backend/src/services/__tests__/todo.service.test.ts`
   - Test: create, findAll, update, delete
   - Mock Prisma client

### Frontend

4. **Configure Testing Library**
   - Add @testing-library/react dependencies
   - Configure jest-dom
   - Add test script to package.json

5. **Create Auth Component Tests**
   - Create `frontend/src/components/auth/__tests__/LoginForm.test.tsx`
   - Test: form rendering, validation, submission

6. **Create Todo Component Tests**
   - Create `frontend/src/components/todos/__tests__/TodoItem.test.tsx`
   - Test: rendering, toggle, delete

## Expected Test Structure

```
backend/src/
└── services/
    └── __tests__/
        ├── auth.service.test.ts
        └── todo.service.test.ts

frontend/src/
└── components/
    ├── auth/
    │   └── __tests__/
    │       └── LoginForm.test.tsx
    └── todos/
        └── __tests__/
            └── TodoItem.test.tsx
```

## Definition of Done
- [ ] Jest configured for backend
- [ ] React Testing Library configured for frontend
- [ ] Auth service tests pass
- [ ] Todo service tests pass
- [ ] Component tests pass
- [ ] Coverage > 70%

## Verification
```bash
# Backend tests
cd backend
pnpm test
pnpm test -- --coverage

# Frontend tests
cd frontend
pnpm test
pnpm test -- --coverage
```

## After Completion
Proceed to: **@context/agents/agent-cicd.md** (Optional)

