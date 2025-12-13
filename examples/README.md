# Context Mesh Examples

This directory contains complete, working examples of Context Mesh in action. Each example demonstrates the full workflow from Intent → Build → Learn with real projects.

## 🎯 Which Example Should I Use?

### 🚀 Start Here: Weather App Minimal

**Best for**: Beginners, quick learning, minimal setup

**[weather-app-minimal/](weather-app-minimal/)** - A minimal Weather App that demonstrates Context Mesh with:
- ✅ **Simple setup**: No database, no Docker, no complex dependencies
- ✅ **Quick implementation**: 45-60 minutes total
- ✅ **Modern stack**: Vite + React + TypeScript + shadcn-ui + Fastify + Swagger
- ✅ **Happy path only**: Focus on learning Context Mesh, not edge cases
- ✅ **Complete workflow**: Intent → Build → Learn fully demonstrated

**Tech Stack**:
- Frontend: Vite + React + TypeScript + shadcn-ui
- Backend: Node.js + Fastify + Swagger
- API: OpenWeatherMap (free tier)

**Prerequisites**:
- Node.js 20+
- OpenWeatherMap API key (free)

**Time**: 45-60 minutes

---

### 📚 Complete Example: Todo App

**Best for**: Learning full Context Mesh, production-like scenarios

**[todo-app-complete/](todo-app-complete/)** - A complete Todo App that demonstrates Context Mesh with:
- ✅ **Full-stack**: Frontend + Backend + Database
- ✅ **Production-ready**: Testing, CI/CD, deployment
- ✅ **Complete features**: Authentication, CRUD, error handling
- ✅ **Best practices**: Docker, GitHub Actions, Railway, Vercel
- ✅ **Comprehensive**: All Context Mesh artifacts demonstrated

**Tech Stack**:
- Frontend: React + TypeScript + Vite
- Backend: Node.js + Express + TypeScript
- Database: PostgreSQL (Docker Compose)
- Testing: Jest + React Testing Library
- CI/CD: GitHub Actions
- Deployment: Railway (backend) + Vercel (frontend)

**Prerequisites**:
- Node.js 18+
- Docker and Docker Compose
- PostgreSQL (via Docker)
- GitHub account (for CI/CD)
- Railway account (for backend deployment)
- Vercel account (for frontend deployment)

**Time**: 2-3 hours

---

## 📊 Comparison

| Aspect | Weather App Minimal | Todo App Complete |
|--------|-------------------|-------------------|
| **Complexity** | Low | High |
| **Setup Time** | 5 minutes | 15-20 minutes |
| **Implementation Time** | 45-60 minutes | 2-3 hours |
| **Database** | None | PostgreSQL |
| **Docker** | No | Yes |
| **Testing** | No | Yes (70% coverage) |
| **CI/CD** | No | Yes (GitHub Actions) |
| **Deployment** | Optional | Yes (Railway + Vercel) |
| **Features** | 1 feature | 4 features |
| **Decisions** | 2 decisions | 7 decisions |
| **Best For** | Learning, quick start | Production patterns, full workflow |

---

## 🚀 Quick Start

### Option 1: Weather App Minimal (Recommended for Beginners)

```bash
cd weather-app-minimal
# Read README.md for step-by-step guide
# Follow Intent → Build → Learn workflow
```

**See**: [weather-app-minimal/README.md](weather-app-minimal/README.md)

### Option 2: Todo App Complete (Recommended for Advanced)

```bash
cd todo-app-complete
# Read README.md for step-by-step guide
# Follow Intent → Build → Learn workflow
```

**See**: [todo-app-complete/README.md](todo-app-complete/README.md)

---

## 📖 What You'll Learn

Both examples teach you:

1. **How to structure Context Mesh** for a project
2. **How to create intent documents** (project, features)
3. **How to document technical decisions** with rationale
4. **How to use Context Mesh workflow** (Intent → Build → Learn)
5. **How AI can generate code** from context files
6. **How to update context** in the Learn phase

### Weather App Minimal Focuses On:
- ✅ Simple Context Mesh structure
- ✅ Basic Intent → Build → Learn workflow
- ✅ Modern tech stack setup
- ✅ API integration patterns

### Todo App Complete Focuses On:
- ✅ Complete Context Mesh structure
- ✅ Advanced Intent → Build → Learn workflow
- ✅ Production patterns (testing, CI/CD, deployment)
- ✅ Database integration
- ✅ Authentication patterns
- ✅ DevOps practices

---

## 📁 Example Structure

Both examples follow the same Context Mesh structure:

```
example-name/
├── README.md                    # Step-by-step guide
├── AGENTS.md                    # Router for AI agents (optional but recommended)
├── context/                     # Context Mesh structure
│   ├── intent/
│   │   ├── project-intent.md   # Overall project intent
│   │   ├── feature-*.md        # Feature intents
│   │   ├── bug-*.md            # Bug fix intents
│   │   └── refactor-*.md      # Refactoring intents
│   ├── decisions/
│   │   └── 001-*.md, 002-*.md  # Technical decisions
│   ├── knowledge/
│   │   ├── patterns/
│   │   │   └── *.md            # Patterns and best practices
│   │   └── anti-patterns/
│   │       └── *.md            # Anti-patterns to avoid
│   └── evolution/
│       ├── changelog.md        # Project changelog
│       └── learning-*.md      # Learnings from implementation
└── [code/]                      # Generated code (optional)
```

---

## 📋 About AGENTS.md

**AGENTS.md** is an optional but recommended file that acts as a router for AI agents, directing them to Context Mesh files for strategic context while providing operational instructions.

### When to Use AGENTS.md

**If your project already has AGENTS.md:**
- ✅ Use the existing `AGENTS.md` file
- ✅ Update it to reference Context Mesh files (see [AGENTS.md.example](../AGENTS.md.example))
- ✅ Ensure it includes a "Context Files to Load" section

**If your project doesn't have AGENTS.md:**
- ✅ Follow the example: [AGENTS.md.example](../AGENTS.md.example)
- ✅ Copy and adapt it to your project needs
- ✅ Include all relevant Context Mesh file references
- ✅ Keep it succinct - it should route to Context Mesh, not duplicate it

### Key Points

- **AGENTS.md** = Operational router (setup, commands, workflow, references to Context Mesh)
- **Context Mesh** = Strategic context (intent, decisions, knowledge, patterns)
- **Together**: Complete guidance for AI agents - both operational (how) and strategic (what, why)

See [TOOLS.md](../TOOLS.md) for more details on AGENTS.md integration.

---

---

## 🎓 Learning Path

### Step 1: Understand Context Mesh
1. Read [FRAMEWORK.md](../FRAMEWORK.md) - Understand the 3-step workflow
2. Read [GETTING_STARTED.md](../GETTING_STARTED.md) - Learn the basics

### Step 2: Try Weather App Minimal
1. Follow [weather-app-minimal/README.md](weather-app-minimal/README.md)
2. Complete Intent → Build → Learn workflow
3. Understand how context drives code generation

### Step 3: Try Todo App Complete (Optional)
1. Follow [todo-app-complete/README.md](todo-app-complete/README.md)
2. See advanced patterns (testing, CI/CD, deployment)
3. Understand production-ready Context Mesh

### Step 4: Apply to Your Project
1. Use the examples as templates
2. Adapt Context Mesh structure to your needs
3. Start with simple prompts, add complexity as needed

---

## 💡 Key Concepts Demonstrated

### Intent Phase
- **Project Intent**: What and why we're building
- **Feature Intents**: Specific feature requirements
- **Technical Decisions**: Technology choices with rationale

### Build Phase
- **Simple Prompts**: Reference context files, not detailed instructions
- **AI Code Generation**: AI reads context and generates code
- **Human Supervision**: Review and validate generated code

### Learn Phase
- **Changelog Updates**: Document what was built
- **Context Updates**: Ensure context reflects actual code
- **Reflection**: Learn from the implementation

---

## 🔗 Related Documentation

- [FRAMEWORK.md](../FRAMEWORK.md) - Complete framework structure
- [GETTING_STARTED.md](../GETTING_STARTED.md) - Getting started guide
- [EXAMPLES.md](../EXAMPLES.md) - More examples and use cases
- [PRINCIPLES.md](../PRINCIPLES.md) - The 5 AI-First principles
- [TOOLS.md](../TOOLS.md) - Tooling recommendations

---

## 🤝 Contributing

Have an example to share? We'd love to include it! Examples should:
- Demonstrate Context Mesh workflow clearly
- Include complete context structure
- Have step-by-step README
- Show Intent → Build → Learn phases

---

**Ready to start?** Choose an example above and follow its README.md!

**New to Context Mesh?** Start with [weather-app-minimal/](weather-app-minimal/) - it's the fastest way to learn!

