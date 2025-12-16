# Agent: Database - Todo App

## Purpose
Configure PostgreSQL with Docker Compose and setup Prisma schema with User and Todo models.

## Context Files to Load
- @context/decisions/003-database-schema.md
- @context/decisions/004-dev-environment.md
- @context/knowledge/patterns/docker-compose.md

## Scope
- **Allowed:** Root project, `backend/prisma/`
- **Prohibited:** Don't implement application logic

## Execution Steps

1. **Create Docker Compose**
   - Create `docker-compose.yml` with PostgreSQL
   - Configure persistent volume
   - Set credentials: user=todoapp, password=todoapp_password, db=todoapp

2. **Create Prisma Schema**
   - Configure datasource for PostgreSQL
   - Create User model (id, email, password, name, createdAt)
   - Create Todo model (id, title, description, completed, userId, createdAt)
   - Configure relations

3. **Run Migrations**
   - Generate initial migration
   - Generate Prisma client

## Expected Output

**docker-compose.yml**
```yaml
services:
  postgres:
    image: postgres:15
    environment:
      POSTGRES_USER: todoapp
      POSTGRES_PASSWORD: todoapp_password
      POSTGRES_DB: todoapp
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

**prisma/schema.prisma**
```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id        String   @id @default(uuid())
  email     String   @unique
  password  String
  name      String?
  createdAt DateTime @default(now())
  todos     Todo[]
}

model Todo {
  id          String   @id @default(uuid())
  title       String
  description String?
  completed   Boolean  @default(false)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
  userId      String
  user        User     @relation(fields: [userId], references: [id])
}
```

## Definition of Done
- [ ] docker-compose.yml created
- [ ] Prisma schema has User and Todo models
- [ ] Relations configured correctly
- [ ] `docker-compose up -d` starts PostgreSQL
- [ ] `npx prisma migrate dev` runs successfully
- [ ] `npx prisma generate` creates client

## Verification
```bash
# Start database
docker-compose up -d

# Check it's running
docker-compose ps

# Run migrations
cd backend
npx prisma migrate dev --name init
npx prisma generate

# Verify with Prisma Studio
npx prisma studio
```

## After Completion
Proceed to: **@context/agents/agent-auth.md**

