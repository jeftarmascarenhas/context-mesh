# Pattern: Unit Testing

## Description

Unit testing pattern for backend API and frontend React components. This pattern defines how to structure tests, what to test, and how to mock dependencies.

## Pattern

### Backend Testing Structure

**File Structure**:
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

**Test Example** (API Route):
```typescript
import request from 'supertest';
import app from '../app';
import { PrismaClient } from '@prisma/client';

// Mock Prisma
jest.mock('@prisma/client', () => ({
  PrismaClient: jest.fn(() => ({
    user: {
      create: jest.fn(),
      findUnique: jest.fn(),
    },
  })),
}));

describe('POST /api/v1/auth/signup', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  it('should create a new user', async () => {
    const mockUser = {
      id: '1',
      email: 'test@example.com',
      name: 'Test User',
      createdAt: new Date(),
    };

    (PrismaClient as jest.Mock).mockImplementation(() => ({
      user: {
        create: jest.fn().mockResolvedValue(mockUser),
      },
    }));

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

  it('should return 400 for invalid email', async () => {
    const response = await request(app)
      .post('/api/v1/auth/signup')
      .send({
        email: 'invalid-email',
        password: 'password123',
      });

    expect(response.status).toBe(400);
    expect(response.body.success).toBe(false);
    expect(response.body.error.code).toBe('VALIDATION_ERROR');
  });
});
```

**Test Example** (Service):
```typescript
import { AuthService } from '../auth.service';
import { PrismaClient } from '@prisma/client';
import bcrypt from 'bcrypt';

jest.mock('@prisma/client');
jest.mock('bcrypt');

describe('AuthService', () => {
  let authService: AuthService;
  let mockPrisma: jest.Mocked<PrismaClient>;

  beforeEach(() => {
    mockPrisma = new PrismaClient() as jest.Mocked<PrismaClient>;
    authService = new AuthService(mockPrisma);
    jest.clearAllMocks();
  });

  describe('signup', () => {
    it('should hash password before saving', async () => {
      const mockUser = {
        id: '1',
        email: 'test@example.com',
        password: 'hashed_password',
      };

      (bcrypt.hash as jest.Mock).mockResolvedValue('hashed_password');
      (mockPrisma.user.create as jest.Mock).mockResolvedValue(mockUser);

      const result = await authService.signup({
        email: 'test@example.com',
        password: 'password123',
        name: 'Test User',
      });

      expect(bcrypt.hash).toHaveBeenCalledWith('password123', 10);
      expect(mockPrisma.user.create).toHaveBeenCalled();
      expect(result).toHaveProperty('id');
    });
  });
});
```

### Frontend Testing Structure

**File Structure**:
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

**Test Example** (React Component):
```typescript
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import { Login } from '../Login';
import * as api from '../../services/api';

// Mock API
jest.mock('../../services/api', () => ({
  api: {
    post: jest.fn(),
  },
}));

describe('Login', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  it('should render login form', () => {
    render(<Login />);

    expect(screen.getByLabelText(/email/i)).toBeInTheDocument();
    expect(screen.getByLabelText(/password/i)).toBeInTheDocument();
    expect(screen.getByRole('button', { name: /login/i })).toBeInTheDocument();
  });

  it('should submit form with email and password', async () => {
    const mockResponse = {
      success: true,
      data: { id: '1', email: 'test@example.com' },
    };

    (api.api.post as jest.Mock).mockResolvedValue({ data: mockResponse });

    render(<Login />);

    fireEvent.change(screen.getByLabelText(/email/i), {
      target: { value: 'test@example.com' },
    });
    fireEvent.change(screen.getByLabelText(/password/i), {
      target: { value: 'password123' },
    });
    fireEvent.click(screen.getByRole('button', { name: /login/i }));

    await waitFor(() => {
      expect(api.api.post).toHaveBeenCalledWith('/auth/login', {
        email: 'test@example.com',
        password: 'password123',
      });
    });
  });

  it('should display error message on login failure', async () => {
    const mockError = {
      success: false,
      error: { message: 'Invalid credentials' },
    };

    (api.api.post as jest.Mock).mockRejectedValue({
      response: { data: mockError },
    });

    render(<Login />);

    fireEvent.change(screen.getByLabelText(/email/i), {
      target: { value: 'test@example.com' },
    });
    fireEvent.change(screen.getByLabelText(/password/i), {
      target: { value: 'wrong' },
    });
    fireEvent.click(screen.getByRole('button', { name: /login/i }));

    await waitFor(() => {
      expect(screen.getByText(/invalid credentials/i)).toBeInTheDocument();
    });
  });
});
```

**Test Example** (Custom Hook):
```typescript
import { renderHook, act } from '@testing-library/react';
import { useAuth } from '../useAuth';

describe('useAuth', () => {
  it('should initialize with null user', () => {
    const { result } = renderHook(() => useAuth());

    expect(result.current.user).toBeNull();
    expect(result.current.isAuthenticated).toBe(false);
  });

  it('should set user on login', async () => {
    const { result } = renderHook(() => useAuth());

    await act(async () => {
      await result.current.login('test@example.com', 'password123');
    });

    expect(result.current.user).not.toBeNull();
    expect(result.current.isAuthenticated).toBe(true);
  });
});
```

## When to Use

- Test API routes and endpoints
- Test service logic
- Test React components
- Test custom hooks
- Test utility functions
- Validate business logic

## What to Test

### Backend
- ✅ API endpoints (request/response)
- ✅ Service methods (business logic)
- ✅ Middleware (authentication, error handling)
- ✅ Validation (DTOs, input validation)
- ❌ Prisma internals (mock instead)
- ❌ Third-party libraries

### Frontend
- ✅ Component rendering
- ✅ User interactions (clicks, form submissions)
- ✅ State changes
- ✅ API integration
- ✅ Custom hooks
- ❌ React internals
- ❌ Third-party libraries

## Mocking Strategy

### Backend Mocking
- **Prisma**: Mock `PrismaClient` and methods
- **External APIs**: Mock HTTP requests
- **JWT**: Mock token generation/verification
- **bcrypt**: Mock password hashing

### Frontend Mocking
- **API Service**: Mock API calls
- **React Router**: Mock navigation
- **Local Storage**: Mock storage operations
- **External Libraries**: Mock as needed

## Best Practices

1. **Arrange-Act-Assert**: Structure tests clearly
2. **Test Behavior**: Test what users see/do, not implementation
3. **Isolation**: Each test should be independent
4. **Mocking**: Mock external dependencies, not code under test
5. **Coverage**: Aim for 70% coverage minimum
6. **Fast Tests**: Tests should run quickly (< 30 seconds total)
7. **Clear Names**: Test names should describe what they test

## Coverage Goals

- **Branches**: 70% minimum
- **Functions**: 70% minimum
- **Lines**: 70% minimum
- **Statements**: 70% minimum

## Related

- [Decision: Testing Strategy](../../decisions/005-testing-strategy.md)
- [Feature: Testing](../../intent/feature-testing.md)
- [Decision: CI/CD Pipeline](../../decisions/006-ci-cd-pipeline.md)

