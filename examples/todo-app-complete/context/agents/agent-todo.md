# Agent: Todo CRUD - Todo App

## Purpose
Implement Todo CRUD operations with create, read, update, delete functionality.

## Context Files to Load
- @context/intent/feature-todo-crud.md
- @context/decisions/003-database-schema.md
- @context/knowledge/patterns/api-design.md
- @context/knowledge/anti-patterns/avoid-direct-db.md

## Scope
- **Allowed:** `backend/src/services/`, `backend/src/routes/`, `backend/src/dto/`
- **Prohibited:** Modify auth logic, modify database schema

## Execution Steps

1. **Create Todo DTOs**
   - Create `backend/src/dto/todo.dto.ts`
   - Define: CreateTodoDto, UpdateTodoDto, TodoResponse

2. **Create Todo Service**
   - Create `backend/src/services/todo.service.ts`
   - Implement: create, findAll, findOne, update, delete
   - Always filter by userId (scoped to user)
   - Use Prisma client, not direct DB access

3. **Create Todo Routes**
   - Create `backend/src/routes/todo.routes.ts`
   - `GET /api/v1/todos` - List user's todos
   - `GET /api/v1/todos/:id` - Get single todo
   - `POST /api/v1/todos` - Create todo
   - `PUT /api/v1/todos/:id` - Update todo
   - `DELETE /api/v1/todos/:id` - Delete todo
   - All routes protected by auth middleware

4. **Register Routes**
   - Add todo routes to `app.ts`

## API Endpoints

```
GET /api/v1/todos
Headers: Cookie: token=JWT
Response: { todos: [...] }

GET /api/v1/todos/:id
Headers: Cookie: token=JWT
Response: { todo: {...} }

POST /api/v1/todos
Headers: Cookie: token=JWT
Body: { title, description? }
Response: { todo: {...} }

PUT /api/v1/todos/:id
Headers: Cookie: token=JWT
Body: { title?, description?, completed? }
Response: { todo: {...} }

DELETE /api/v1/todos/:id
Headers: Cookie: token=JWT
Response: { message: "Deleted" }
```

## Definition of Done
- [ ] Todo service implements all CRUD operations
- [ ] Todos scoped to authenticated user
- [ ] All routes protected by auth middleware
- [ ] Proper error handling (404, 403)
- [ ] DTOs validate input data
- [ ] Uses service layer pattern (no direct DB in routes)

## Verification
```bash
cd backend && pnpm run dev

# Create todo (need to login first and use token)
curl -X POST http://localhost:3000/api/v1/todos \
  -H "Content-Type: application/json" \
  -H "Cookie: token=YOUR_JWT" \
  -d '{"title":"Test","description":"Test desc"}'

# List todos
curl http://localhost:3000/api/v1/todos \
  -H "Cookie: token=YOUR_JWT"

# Update todo
curl -X PUT http://localhost:3000/api/v1/todos/TODO_ID \
  -H "Content-Type: application/json" \
  -H "Cookie: token=YOUR_JWT" \
  -d '{"completed":true}'

# Delete todo
curl -X DELETE http://localhost:3000/api/v1/todos/TODO_ID \
  -H "Cookie: token=YOUR_JWT"
```

## After Completion
Proceed to: **@context/agents/agent-frontend.md**

