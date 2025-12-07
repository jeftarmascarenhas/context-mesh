# Decision: Development Environment Setup

## Context

We need to set up a development environment that:
- Works consistently across different machines
- Is easy to set up for new developers
- Separates local development from production
- Uses Docker for database to avoid local PostgreSQL installation
- Provides clear prerequisites and setup instructions

## Decision

**Development Environment**:

1. **Docker Compose for PostgreSQL**:
   - PostgreSQL 15+ running in Docker container
   - Only database runs in Docker (not application)
   - Persistent volume for data
   - Environment variables for configuration

2. **Prerequisites** (must be installed locally):
   - Node.js 18+ (for running backend and frontend)
   - Docker and Docker Compose (for PostgreSQL database)
   - Git (for version control)
   - npm or yarn (comes with Node.js)

3. **Local Development**:
   - Backend runs directly with `npm run dev` (not in Docker)
   - Frontend runs directly with `npm run dev` (not in Docker)
   - Database runs in Docker via `docker-compose up -d`
   - Environment variables in `.env` files (not committed to Git)

4. **Environment Variables**:
   - `.env.example` files in both backend and frontend
   - `.env` files in `.gitignore`
   - Clear documentation of required variables

## Rationale

1. **Docker for Database Only**: 
   - Avoids PostgreSQL installation complexity
   - Consistent database version across team
   - Easy to reset database (just remove volume)
   - Application runs natively for faster development

2. **Native Application Execution**:
   - Faster development (no Docker overhead)
   - Easier debugging (direct access to Node.js)
   - Better IDE integration
   - Hot reload works better

3. **Clear Prerequisites**:
   - Developers know exactly what to install
   - Reduces setup friction
   - Works on macOS, Linux, and Windows

4. **Environment Variables**:
   - Security (secrets not in code)
   - Easy configuration per environment
   - Clear documentation via `.env.example`

## Alternatives Considered

### Alternative 1: Full Docker Compose (App + Database)
- **Pros**: Complete isolation, works everywhere
- **Cons**: Slower development, harder debugging, more complex
- **Why Not Chosen**: Native execution is faster for development, Docker only needed for database

### Alternative 2: Local PostgreSQL Installation
- **Pros**: No Docker needed
- **Cons**: Installation complexity varies by OS, version conflicts
- **Why Not Chosen**: Docker Compose is simpler and more consistent

### Alternative 3: SQLite for Development
- **Pros**: No database server needed
- **Cons**: Different from production (PostgreSQL), migration issues
- **Why Not Chosen**: Use same database as production to avoid issues

## Implementation Details

### Docker Compose Configuration

**File**: `docker-compose.yml` (project root)

```yaml
version: '3.8'

services:
  postgres:
    image: postgres:15-alpine
    container_name: todo-app-postgres
    environment:
      POSTGRES_USER: todoapp
      POSTGRES_PASSWORD: todoapp_password
      POSTGRES_DB: todoapp
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U todoapp"]
      interval: 10s
      timeout: 5s
      retries: 5

volumes:
  postgres_data:
```

**Connection String**:
```
DATABASE_URL=postgresql://todoapp:todoapp_password@localhost:5432/todoapp
```

### Commands

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

### Prerequisites Checklist

Before starting development, ensure:
- [ ] Node.js 18+ installed (`node --version`)
- [ ] npm installed (`npm --version`)
- [ ] Docker installed (`docker --version`)
- [ ] Docker Compose installed (`docker-compose --version`)
- [ ] Git installed (`git --version`)

## Outcomes

**After Implementation**:
- ✅ Docker Compose setup was straightforward
- ✅ Database runs consistently across different machines
- ✅ No need to install PostgreSQL locally
- ✅ Easy to reset database for testing
- ✅ Clear prerequisites reduced setup issues

**Lessons Learned**:
- Docker Compose for database only is the right balance
- Native app execution is faster for development
- Clear prerequisites prevent setup issues

## Related

- [Decision: Tech Stack](001-tech-stack.md)
- [Decision: Database Schema](003-database-schema.md)
- [Pattern: Docker Compose](../knowledge/patterns/docker-compose.md)

## Status

- **Created**: 2025-12-05 (Phase: Intent)
- **Status**: Accepted

