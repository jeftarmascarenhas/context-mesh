# Decision: Testing Strategy

## Context

We need to implement testing for the Todo application to ensure:
- Code quality and reliability
- Regression prevention
- Confidence in refactoring
- CI/CD pipeline validation
- Meet project acceptance criteria (70% code coverage)

## Decision

**Testing Strategy**:

1. **Unit Tests**:
   - **Backend**: Jest for API routes, services, middleware, and utilities
   - **Frontend**: Jest + React Testing Library for components and hooks
   - **Coverage Target**: Minimum 70% code coverage
   - **Test Location**: `__tests__` directories or `.test.ts`/`.test.tsx` files

2. **Test Structure**:
   - **Backend**: Tests mirror source structure (`src/routes/__tests__/`, `src/services/__tests__/`)
   - **Frontend**: Tests next to components (`components/__tests__/`) or in `__tests__` directories
   - **Fixtures**: Shared test data in `__fixtures__` or `__mocks__` directories

3. **Testing Tools**:
   - **Jest**: Test runner and assertion library
   - **React Testing Library**: Component testing utilities
   - **@testing-library/user-event**: User interaction simulation
   - **supertest**: HTTP assertions for API testing
   - **@prisma/client**: Mock Prisma client for database operations

4. **What to Test**:
   - **Backend**: API endpoints, service logic, middleware, validation
   - **Frontend**: Component rendering, user interactions, API integration, hooks
   - **Not Testing**: Third-party libraries, Prisma internals, React internals

5. **Test Execution**:
   - **Local**: `npm test` (watch mode) or `npm test -- --coverage`
   - **CI/CD**: `npm test -- --coverage --ci` (runs once, generates coverage)

## Rationale

1. **Jest**: Industry standard, excellent TypeScript support, built-in mocking
2. **React Testing Library**: Encourages testing user behavior, not implementation
3. **70% Coverage**: Good balance between quality and development speed
4. **Unit Tests Focus**: Fast, reliable, easy to maintain
5. **Test Structure**: Clear organization, easy to find tests

## Alternatives Considered

### Alternative 1: Integration Tests Only
- **Pros**: Tests real behavior, catches integration issues
- **Cons**: Slower, harder to debug, more setup required
- **Why Not Chosen**: Unit tests are faster and catch most issues, integration tests can be added later

### Alternative 2: E2E Tests (Playwright, Cypress)
- **Pros**: Tests complete user flows
- **Cons**: Very slow, flaky, complex setup
- **Why Not Chosen**: Unit tests are sufficient for MVP, E2E can be added in Phase 2

### Alternative 3: No Tests
- **Pros**: Faster initial development
- **Cons**: No quality assurance, risky refactoring, no CI/CD validation
- **Why Not Chosen**: Tests are essential for maintainable code and CI/CD

## Implementation Details

### Backend Testing

**Test Example Structure**:
```
backend/
├── src/
│   ├── routes/
│   │   ├── auth.routes.ts
│   │   └── __tests__/
│   │       └── auth.routes.test.ts
│   ├── services/
│   │   ├── auth.service.ts
│   │   └── __tests__/
│   │       └── auth.service.test.ts
│   └── middleware/
│       ├── auth.middleware.ts
│       └── __tests__/
│           └── auth.middleware.test.ts
```

**Jest Configuration** (`jest.config.js`):
```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
  coverageDirectory: 'coverage',
  collectCoverageFrom: [
    'src/**/*.ts',
    '!src/**/*.d.ts',
    '!src/**/__tests__/**',
  ],
  coverageThreshold: {
    global: {
      branches: 70,
      functions: 70,
      lines: 70,
      statements: 70,
    },
  },
};
```

**Test Example** (API Route):
```typescript
import request from 'supertest';
import app from '../app';

describe('POST /api/v1/auth/signup', () => {
  it('should create a new user', async () => {
    const response = await request(app)
      .post('/api/v1/auth/signup')
      .send({
        email: 'test@example.com',
        password: 'password123',
        name: 'Test User',
      });

    expect(response.status).toBe(201);
    expect(response.body.success).toBe(true);
    expect(response.body.data).toHaveProperty('id');
    expect(response.body.data.email).toBe('test@example.com');
  });
});
```

### Frontend Testing

**Test Example Structure**:
```
frontend/
├── src/
│   ├── components/
│   │   ├── auth/
│   │   │   ├── Login.tsx
│   │   │   └── __tests__/
│   │   │       └── Login.test.tsx
│   │   └── todos/
│   │       ├── TodoList.tsx
│   │       └── __tests__/
│   │           └── TodoList.test.tsx
```

**Jest Configuration** (`jest.config.js`):
```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: ['<rootDir>/src/setupTests.ts'],
  moduleNameMapper: {
    '^@/(.*)$': '<rootDir>/src/$1',
  },
  coverageDirectory: 'coverage',
  collectCoverageFrom: [
    'src/**/*.{ts,tsx}',
    '!src/**/*.d.ts',
    '!src/**/__tests__/**',
    '!src/main.tsx',
  ],
  coverageThreshold: {
    global: {
      branches: 70,
      functions: 70,
      lines: 70,
      statements: 70,
    },
  },
};
```

**Test Example** (React Component):
```typescript
import { render, screen, fireEvent } from '@testing-library/react';
import { TodoItem } from '../TodoItem';

describe('TodoItem', () => {
  it('should render todo item', () => {
    const todo = {
      id: '1',
      title: 'Test Todo',
      completed: false,
    };

    render(<TodoItem todo={todo} />);

    expect(screen.getByText('Test Todo')).toBeInTheDocument();
  });

  it('should toggle completion on click', () => {
    const todo = { id: '1', title: 'Test', completed: false };
    const onToggle = jest.fn();

    render(<TodoItem todo={todo} onToggle={onToggle} />);

    fireEvent.click(screen.getByRole('checkbox'));
    expect(onToggle).toHaveBeenCalledWith('1');
  });
});
```

### Mocking Strategy

**Prisma Mock** (Backend):
```typescript
import { PrismaClient } from '@prisma/client';

jest.mock('@prisma/client', () => ({
  PrismaClient: jest.fn(() => ({
    user: {
      create: jest.fn(),
      findUnique: jest.fn(),
    },
  })),
}));
```

**API Mock** (Frontend):
```typescript
jest.mock('../services/api', () => ({
  api: {
    get: jest.fn(),
    post: jest.fn(),
    put: jest.fn(),
    delete: jest.fn(),
  },
}));
```

## Outcomes

**After Implementation**:
- ✅ Unit tests provide confidence in code changes
- ✅ 70% coverage target is achievable
- ✅ Tests catch bugs before deployment
- ✅ CI/CD pipeline validates code quality
- ⚠️ Some edge cases require integration tests (acceptable for MVP)

**Lessons Learned**:
- Unit tests are essential for maintainable code
- React Testing Library encourages better component design
- Mocking Prisma requires careful setup
- Coverage threshold ensures quality standards

## Related

- [Feature: Testing](../intent/feature-testing.md)
- [Pattern: Testing](../knowledge/patterns/testing.md)
- [Decision: CI/CD Pipeline](006-ci-cd-pipeline.md)
- [Project Intent](../intent/project-intent.md)

## Status

- **Created**: 2025-12-05 (Phase: Intent)
- **Status**: Accepted

