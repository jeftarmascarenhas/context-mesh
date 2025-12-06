# Complete Example: Todo App with Context Mesh

This is a **complete end-to-end example** demonstrating how to use Context Mesh in a real project. This example shows the full workflow from Intent to Build to Learn.

## 📋 Overview

**Project**: Simple Todo Application  
**Tech Stack**: React + TypeScript + Node.js + PostgreSQL  
**Duration**: Complete workflow demonstration

## 🎯 What You'll Learn

- How to structure Context Mesh for a real project
- How to create intent documents (project, features, bugs)
- How to document decisions during development
- How to update context in the Learn phase
- How to handle the complete workflow cycle

## 📁 Project Structure

```
todo-app-complete/
├── README.md                    # This file
├── context/                     # Context Mesh structure
│   ├── intent/
│   │   ├── project-intent.md   # Overall project intent
│   │   ├── feature-user-auth.md # Feature: User authentication
│   │   ├── feature-todo-crud.md # Feature: Todo CRUD operations
│   │   └── bug-todo-persistence.md # Bug: Todo persistence issue
│   ├── decisions/
│   │   ├── 001-tech-stack.md    # Decision: Technology stack
│   │   ├── 002-auth-approach.md # Decision: Authentication approach
│   │   └── 003-database-schema.md # Decision: Database schema
│   ├── knowledge/
│   │   ├── patterns/
│   │   │   └── api-design.md   # Pattern: API design
│   │   └── anti-patterns/
│   │       └── avoid-direct-db.md # Anti-pattern: Direct DB access
│   └── evolution/
│       ├── changelog.md         # Project changelog
│       └── learning-001-auth.md # Learning: Authentication insights
└── code/                        # Generated code (example structure)
    ├── frontend/
    ├── backend/
    └── database/
```

## 🚀 Workflow Demonstration

This example demonstrates the complete Context Mesh workflow:

### Phase 1: Intent (Planning)

1. **Project Intent** → `context/intent/project-intent.md`
2. **Feature Intents** → `context/intent/feature-*.md`
3. **Technical Decisions** → `context/decisions/001-*.md`

### Phase 2: Build (Construction)

1. **AI generates code** based on context
2. **Decisions documented** as implementation progresses
3. **Context updated** with implementation details

### Phase 3: Learn (Learning)

1. **Context updated** to reflect actual code
2. **Learnings documented** → `context/evolution/learning-*.md`
3. **Decisions updated** with outcomes
4. **Intent refined** based on learnings

## 📖 How to Use This Example

1. **Read the files in order**:
   - Start with `context/intent/project-intent.md`
   - Then read feature intents
   - Review decisions
   - Check learnings

2. **Follow the workflow**:
   - See how Intent → Build → Learn flows
   - Notice how context evolves
   - Observe decision documentation

3. **Adapt to your project**:
   - Use as a template
   - Modify structure as needed
   - Keep it simple

## 🎓 Key Takeaways

- **Intent drives everything**: Clear intent makes Build faster
- **Decisions in Intent phase**: Planning decisions early speeds up Build
- **Context evolves**: Update context continuously, not just at the end
- **Learnings feed back**: Learnings refine intent for next iteration

## 📚 Related Documentation

- [FRAMEWORK.md](../../FRAMEWORK.md) - Complete framework structure
- [GETTING_STARTED.md](../../GETTING_STARTED.md) - Getting started guide
- [EXAMPLES.md](../../EXAMPLES.md) - More examples

---

**Note**: This is a demonstration example. In a real project, you would have actual code files. The structure and workflow shown here are what you would follow in your own projects.

