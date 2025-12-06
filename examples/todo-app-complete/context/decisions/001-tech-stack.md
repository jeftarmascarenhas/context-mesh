# Decision: Technology Stack

## Context

We need to choose the technology stack for the Todo application. The stack must:
- Support rapid development with AI assistance
- Be modern and maintainable
- Work well with TypeScript
- Have good ecosystem and community support
- Be suitable for full-stack development

## Decision

**Frontend**:
- React 18+ with TypeScript
- Vite for build tooling
- React Router for routing
- Axios for API calls

**Backend**:
- Node.js with Express
- TypeScript
- Prisma ORM for database access
- JWT for authentication

**Database**:
- PostgreSQL (local development)
- Prisma for migrations and schema management

**Development Tools**:
- ESLint + Prettier for code quality
- Jest for testing (backend and frontend)
- React Testing Library for frontend component testing
- Supertest for API testing
- GitHub Actions for CI/CD
- Docker Compose for local PostgreSQL database
- Git for version control

## Rationale

1. **TypeScript**: Provides type safety and better AI code generation
2. **React + Vite**: Fast development, great DX, excellent AI tool support
3. **Express**: Simple, flexible, well-documented
4. **Prisma**: Type-safe database access, excellent migrations
5. **PostgreSQL**: Reliable, feature-rich, free tier available

## Alternatives Considered

### Alternative 1: Next.js (Full-stack)
- **Pros**: Built-in API routes, SSR, great DX
- **Cons**: More complex, might be overkill for MVP
- **Why Not Chosen**: Simpler stack preferred for learning Context Mesh

### Alternative 2: MongoDB
- **Pros**: Flexible schema, easy to start
- **Cons**: Less structured, harder to maintain
- **Why Not Chosen**: PostgreSQL provides better structure and relationships

### Alternative 3: NestJS
- **Pros**: Enterprise-grade, great architecture
- **Cons**: More boilerplate, steeper learning curve
- **Why Not Chosen**: Express is simpler for MVP, can migrate later

## Outcomes

**After Implementation**:
- ✅ TypeScript provided excellent type safety
- ✅ Prisma made database work smooth
- ✅ React + Vite had fast development cycle
- ⚠️ Express required more manual setup than NestJS (acceptable for MVP)
- ✅ Stack worked well with AI code generation

**Lessons Learned**:
- TypeScript + Prisma combination is excellent for AI-assisted development
- Simple stack allowed focus on Context Mesh workflow
- Can migrate to Next.js or NestJS later if needed

## Related

- [Project Intent](../intent/project-intent.md)
- [Decision: Authentication Approach](002-auth-approach.md)
- [Decision: Database Schema](003-database-schema.md)
- [Decision: Dev Environment](004-dev-environment.md)
- [Decision: Testing Strategy](005-testing-strategy.md)
- [Decision: CI/CD Pipeline](006-ci-cd-pipeline.md)

## Status

- **Created**: 2024-01-15 (Intent phase)
- **Status**: Accepted
- **Updated**: 2024-01-20 (Learn phase - added outcomes)

