# Testing Guide: Todo App

Quick validation that the example works correctly.

## Prerequisites

- [ ] Node.js 18+
- [ ] Docker
- [ ] Cursor or GitHub Copilot

## Quick Test

### 1. Validate Context Structure

```bash
cd examples/todo-app-complete

# Check all context files exist
ls context/intent/
ls context/decisions/
ls context/agents/
```

Expected: All files from EXECUTION_GUIDE.md structure exist.

### 2. Test AI Context Loading

In Cursor Chat:
```
Read @context/intent/project-intent.md and summarize what this project is about.
```

Expected: AI correctly identifies Todo App with auth and CRUD.

### 3. Execute Phase 1

```
Execute @context/agents/agent-setup.md
```

Verify:
- [ ] Backend structure created
- [ ] Frontend structure created
- [ ] `pnpm install` works in both

### 4. Continue with Remaining Phases

Follow [EXECUTION_GUIDE.md](EXECUTION_GUIDE.md) for complete test.

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Context doesn't load | Reference files with @context/... |
| Database won't start | Run `docker-compose down -v` then `up -d` |
| Build fails | Check TypeScript errors with `pnpm run build` |
| API errors | Check .env file has all variables |

## Acceptance Criteria

- [ ] All phases complete
- [ ] Build passes
- [ ] App runs locally
- [ ] Can signup, login, create/edit/delete todos
