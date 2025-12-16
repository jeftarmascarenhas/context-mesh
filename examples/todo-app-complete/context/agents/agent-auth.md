# Agent: Authentication - Todo App

## Purpose
Implement user authentication with JWT, including signup, login, and logout functionality.

## Context Files to Load
- @context/intent/feature-user-auth.md
- @context/decisions/002-auth-approach.md
- @context/knowledge/patterns/api-design.md
- @context/knowledge/anti-patterns/avoid-direct-db.md

## Scope
- **Allowed directories:** `backend/src/`, `frontend/src/`
- **Prohibited:** Don't modify database schema

## Execution Steps

### Backend

1. **Create Auth Service**
   - Create `backend/src/services/auth.service.ts`
   - Implement: signup, login, validateToken
   - Use bcrypt for password hashing
   - Use JWT for tokens

2. **Create Auth DTOs**
   - Create `backend/src/dto/auth.dto.ts`
   - Define: SignupDto, LoginDto, AuthResponse

3. **Create Auth Middleware**
   - Create `backend/src/middleware/auth.middleware.ts`
   - Verify JWT token
   - Attach user to request

4. **Create Auth Routes**
   - Create `backend/src/routes/auth.routes.ts`
   - `POST /api/auth/signup`
   - `POST /api/auth/login`
   - `POST /api/auth/logout`
   - Register routes in `app.ts`

### Frontend

5. **Create Auth Context**
   - Create `frontend/src/context/AuthContext.tsx`
   - Manage user state and tokens
   - Provide login, logout, signup methods

6. **Create Auth Components**
   - Create `frontend/src/components/auth/Login.tsx`
   - Create `frontend/src/components/auth/Signup.tsx`
   - Create `frontend/src/components/auth/Logout.tsx`

7. **Create Auth Pages**
   - Create `frontend/src/pages/Login.tsx`
   - Create `frontend/src/pages/Signup.tsx`

8. **Create API Service**
   - Create `frontend/src/services/api.ts`
   - Configure Axios with auth interceptor

## API Endpoints

```
POST /api/auth/signup
Body: { email, password, name }
Response: { user: { id, email, name }, token }

POST /api/auth/login
Body: { email, password }
Response: { user: { id, email, name }, token }

POST /api/auth/logout
Response: { message: "Logged out" }
```

## Definition of Done
- [ ] Auth service handles signup, login, logout
- [ ] Passwords are hashed with bcrypt
- [ ] JWT tokens are generated and validated
- [ ] Auth middleware protects routes
- [ ] Frontend AuthContext manages state
- [ ] Login/Signup forms work
- [ ] Token stored in httpOnly cookie or localStorage
- [ ] Protected routes redirect to login

## Verification
```bash
# Backend test
curl -X POST http://localhost:3000/api/auth/signup \
  -H "Content-Type: application/json" \
  -d '{"email":"test@test.com","password":"password123","name":"Test"}'

# Frontend test
# Open app, signup, login, verify redirect to home
```

## After Completion
Proceed to: **@context/agents/agent-crud.md**

