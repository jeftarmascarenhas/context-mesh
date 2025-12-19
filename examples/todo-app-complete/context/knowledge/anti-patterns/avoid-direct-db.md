# Anti-Pattern: Direct Database Access from Controllers

## Description

**Anti-Pattern**: Accessing the database directly from controller/route handlers instead of using a service layer or repository pattern.

## Example (Bad)

```typescript
// ❌ BAD: Direct database access in controller
app.post('/api/todos', async (req, res) => {
  const todo = await prisma.todo.create({
    data: {
      title: req.body.title,
      userId: req.user.id
    }
  });
  res.json(todo);
});
```

## Problems

1. **No Business Logic Separation**: Business logic mixed with HTTP handling
2. **Hard to Test**: Difficult to mock database calls
3. **Code Duplication**: Same database logic repeated across controllers
4. **Hard to Maintain**: Changes require updating multiple places

## Solution (Good)

```typescript
// ✅ GOOD: Service layer handles business logic
// services/todoService.ts
export class TodoService {
  async createTodo(userId: string, data: CreateTodoDto) {
    return await prisma.todo.create({
      data: {
        ...data,
        userId
      }
    });
  }
}

// controllers/todoController.ts
app.post('/api/todos', async (req, res) => {
  const todo = await todoService.createTodo(req.user.id, req.body);
  res.json(todo);
});
```

## When to Avoid

- Always avoid direct database access in controllers
- Use service layer or repository pattern
- Keep controllers thin (only HTTP handling)

## Related

- [Pattern: API Design](../patterns/api-design.md)
- [Decision: Tech Stack](../../decisions/001-tech-stack.md)

