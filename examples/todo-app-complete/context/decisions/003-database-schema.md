# Decision: Database Schema Design

## Context

We need to design the database schema for the Todo application. The schema must support:
- User authentication (users table)
- Todo items with user association
- Categories for organizing todos
- Timestamps for tracking creation/updates

## Decision

**Database Schema**:

```prisma
model User {
  id        String   @id @default(uuid())
  email     String   @unique
  password  String   // hashed with bcrypt
  name      String?
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  todos     Todo[]
}

model Todo {
  id          String   @id @default(uuid())
  title       String
  description String?
  completed   Boolean  @default(false)
  category    String?
  userId      String
  user        User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
}
```

**Key Design Decisions**:
- UUID primary keys (better than auto-increment for distributed systems)
- Cascade delete (when user deleted, todos deleted)
- Optional description and category (flexibility)
- Timestamps for audit trail

## Rationale

1. **Simple and Focused**: Only what's needed for MVP
2. **User-Todo Relationship**: Clear foreign key relationship
3. **Cascade Delete**: Prevents orphaned todos
4. **UUID**: Better for distributed systems, security (no ID enumeration)
5. **Timestamps**: Useful for sorting, filtering, audit

## Alternatives Considered

### Alternative 1: Separate Categories Table
- **Pros**: Normalized, can add category metadata later
- **Cons**: More complex, requires joins
- **Why Not Chosen**: Simple string category is sufficient for MVP, can normalize later

### Alternative 2: Auto-increment IDs
- **Pros**: Simpler, smaller storage
- **Cons**: Security risk (ID enumeration), harder to merge databases
- **Why Not Chosen**: UUID is better for security and scalability

### Alternative 3: Soft Deletes
- **Pros**: Can recover deleted todos
- **Cons**: More complex queries, need deletedAt field
- **Why Not Chosen**: Hard deletes are simpler for MVP, can add soft deletes later

## Outcomes

**After Implementation**:
- ✅ Schema was simple and easy to work with
- ✅ Prisma migrations were smooth
- ✅ Cascade delete worked as expected
- ✅ UUIDs provided good security (no ID enumeration)
- ⚠️ Category as string worked but might need normalization later
- ✅ Timestamps were useful for sorting and filtering

**Lessons Learned**:
- Simple schema was perfect for MVP
- Prisma made schema changes easy
- Can add category table later if needed
- UUIDs were worth the extra storage

## Related

- [Project Intent](../intent/project-intent.md)
- [Feature: Todo CRUD](../intent/feature-todo-crud.md)
- [Decision: Tech Stack](001-tech-stack.md)

## Status

- **Created**: 2025-12-02 (Phase: Intent)
- **Status**: Accepted
- **Updated**: 2025-12-05 (Phase: Learn) - Added outcomes

