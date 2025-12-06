# Pattern: API Design

## Description

RESTful API design pattern for the Todo application. This pattern defines how we structure API endpoints, request/response formats, and error handling.

## Pattern

### Endpoint Structure

```
/api/v1/auth/signup     POST   - User registration
/api/v1/auth/login      POST   - User login
/api/v1/auth/logout     POST   - User logout
/api/v1/todos           GET    - List all user's todos
/api/v1/todos           POST   - Create new todo
/api/v1/todos/:id       GET    - Get single todo
/api/v1/todos/:id       PUT    - Update todo
/api/v1/todos/:id       DELETE - Delete todo
```

### Request/Response Format

**Request**:
```json
{
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "category": "Shopping"
}
```

**Success Response** (200/201):
```json
{
  "success": true,
  "data": {
    "id": "uuid",
    "title": "Buy groceries",
    "description": "Milk, eggs, bread",
    "category": "Shopping",
    "completed": false,
    "createdAt": "2024-01-15T10:00:00Z"
  }
}
```

**Error Response** (400/401/404/500):
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Title is required",
    "details": {
      "field": "title",
      "reason": "required"
    }
  }
}
```

### Error Codes

- `VALIDATION_ERROR` (400) - Invalid input data
- `UNAUTHORIZED` (401) - Authentication required
- `FORBIDDEN` (403) - Insufficient permissions
- `NOT_FOUND` (404) - Resource not found
- `INTERNAL_ERROR` (500) - Server error

## When to Use

- All API endpoints in the application
- Consistent error handling
- Standard request/response format

## Benefits

- **Consistency**: All endpoints follow same pattern
- **Predictability**: Developers know what to expect
- **Error Handling**: Clear error messages
- **Type Safety**: TypeScript types match API structure

## Examples

See implementation in:
- Backend API routes
- Frontend API client
- Error handling middleware

## Related

- [Feature: Todo CRUD](../intent/feature-todo-crud.md)
- [Decision: Tech Stack](../decisions/001-tech-stack.md)

