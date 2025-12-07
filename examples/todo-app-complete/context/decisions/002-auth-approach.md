# Decision: Authentication Approach

## Context

We need to implement user authentication for the Todo application. Users must be able to sign up, log in, and maintain authenticated sessions. We need to choose between:
- JWT tokens
- Session-based authentication
- OAuth providers (Google, GitHub, etc.)

## Decision

**Use JWT (JSON Web Tokens) for authentication**:
- JWT tokens stored in httpOnly cookies (production) or localStorage (development)
- Token expiration: 7 days
- Refresh token mechanism (future enhancement)
- Password hashing with bcrypt (10 rounds)

**Implementation**:
- Backend: JWT generation and validation middleware
- Frontend: Store token and include in API requests
- Security: httpOnly cookies prevent XSS attacks

## Rationale

1. **Stateless**: No server-side session storage needed
2. **Scalable**: Works well with multiple servers/containers
3. **Simple**: Easier to implement than OAuth for MVP
4. **Secure**: httpOnly cookies prevent XSS, tokens can be revoked (future)

## Alternatives Considered

### Alternative 1: Session-based Authentication
- **Pros**: Simple, tokens can be revoked immediately
- **Cons**: Requires server-side session storage, not scalable
- **Why Not Chosen**: Stateless JWT is better for scalability

### Alternative 2: OAuth (Google, GitHub)
- **Pros**: Users don't need to create accounts, better UX
- **Cons**: More complex, requires OAuth setup, external dependency
- **Why Not Chosen**: Can add later, email/password is sufficient for MVP

### Alternative 3: Magic Links (Passwordless)
- **Pros**: No passwords, better security
- **Cons**: Requires email service, more complex flow
- **Why Not Chosen**: Email/password is simpler for MVP

## Outcomes

**After Implementation**:
- ✅ JWT implementation was straightforward
- ✅ httpOnly cookies worked well (after initial localStorage approach)
- ⚠️ Token refresh not implemented (acceptable for MVP)
- ✅ Password hashing with bcrypt was simple with Prisma
- ✅ Authentication middleware was easy to add to Express routes

**Lessons Learned**:
- httpOnly cookies are better than localStorage for production
- JWT expiration should be shorter for production (we used 7 days for MVP)
- Refresh token mechanism should be added in Phase 2

## Related

- [Feature: User Authentication](../intent/feature-user-auth.md)
- [Decision: Tech Stack](001-tech-stack.md)
- [Learning: Authentication Insights](../evolution/learning-001-auth.md)

## Status

- **Created**: 2025-12-02 (Phase: Intent)
- **Status**: Accepted
- **Updated**: 2025-12-04 (Phase: Learn) - Added outcomes

