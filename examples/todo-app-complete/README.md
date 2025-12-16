# Todo App Complete

A complete Todo App demonstrating full Context Mesh workflow with authentication, testing, and CI/CD.

| Aspect | Details |
|--------|---------|
| **Time** | 2-3 hours |
| **Complexity** | High |
| **Stack** | React + TypeScript + Vite, Express + Prisma + PostgreSQL |
| **Prerequisites** | Node.js 18+, Docker, Git |

## Start Here

👉 **[EXECUTION_GUIDE.md](EXECUTION_GUIDE.md)** - Step-by-step execution guide

## What You'll Build

- Full-stack Todo application with user authentication
- PostgreSQL database with Prisma ORM
- Unit tests with Jest and React Testing Library
- CI/CD with GitHub Actions
- Deployment ready (Railway + Vercel)

## Phases

| Phase | Agent | Description |
|-------|-------|-------------|
| 1 | agent-setup.md | Project structure and configuration |
| 2 | agent-database.md | PostgreSQL + Prisma setup |
| 3 | agent-auth.md | User authentication with JWT |
| 4 | agent-todo.md | Todo CRUD operations |
| 5 | agent-frontend.md | React UI components |
| 6 | agent-testing.md | Unit tests (optional) |
| 7 | agent-cicd.md | GitHub Actions (optional) |

## Quick Start

```bash
# 1. Ensure Docker is running

# 2. Follow the execution guide
cat EXECUTION_GUIDE.md
```

## Context Structure

```
context/
├── intent/
│   ├── project-intent.md
│   ├── feature-user-auth.md
│   ├── feature-todo-crud.md
│   ├── feature-testing.md
│   └── feature-ci-cd.md
├── decisions/
│   ├── 001-tech-stack.md
│   ├── 002-auth-approach.md
│   ├── 003-database-schema.md
│   └── ...
├── knowledge/
│   ├── patterns/
│   └── anti-patterns/
├── agents/
│   ├── agent-setup.md
│   ├── agent-database.md
│   ├── agent-auth.md
│   ├── agent-todo.md
│   ├── agent-frontend.md
│   ├── agent-testing.md
│   └── agent-cicd.md
└── evolution/
    └── changelog.md
```

## Related

- [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) - Execution steps
- [AGENTS.md](AGENTS.md) - AI agent router
- [Weather App Minimal](../weather-app-minimal/) - Quick example
- [Framework Documentation](../../FRAMEWORK.md)
