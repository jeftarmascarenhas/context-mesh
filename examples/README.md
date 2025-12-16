# Context Mesh Examples

Complete, working examples demonstrating the Context Mesh workflow.

## Choose Your Example

| Example | Time | Complexity | Best For |
|---------|------|------------|----------|
| [Weather App Minimal](weather-app-minimal/) | 45-60 min | Low | Beginners, quick learning |
| [Todo App Complete](todo-app-complete/) | 2-3 hours | High | Full workflow, production patterns |

---

## Quick Start

### Weather App Minimal (Recommended for Beginners)

```bash
cd weather-app-minimal
# Follow EXECUTION_GUIDE.md
```

**Phases**: Setup → Backend → Frontend → Done

### Todo App Complete

```bash
cd todo-app-complete
# Follow EXECUTION_GUIDE.md
```

**Phases**: Setup → Database → Auth → Todo CRUD → Testing → CI/CD → Done

---

## What You'll Learn

- How to structure Context Mesh for a project
- How to use agents to execute each phase
- How Intent → Build → Learn workflow works
- How AI generates code from context files

---

## Example Structure

Both examples follow this structure:

```
example-name/
├── EXECUTION_GUIDE.md      # Step-by-step execution (START HERE)
├── AGENTS.md               # Router for AI agents
├── context/
│   ├── intent/             # What and why
│   ├── decisions/          # Technical decisions
│   ├── knowledge/          # Patterns
│   ├── agents/             # Execution agents
│   └── evolution/          # Changelog
└── README.md               # Overview
```

---

## How to Use

1. **Choose an example** based on your experience level
2. **Read EXECUTION_GUIDE.md** in the example folder
3. **Execute phase by phase** following the guide
4. **Verify each phase** before proceeding

---

## Related Documentation

- [FRAMEWORK.md](../FRAMEWORK.md) - Framework structure
- [GETTING_STARTED.md](../GETTING_STARTED.md) - Getting started guide
- [EXAMPLES.md](../EXAMPLES.md) - More examples and use cases

---

**Start here**: [weather-app-minimal/](weather-app-minimal/) for beginners or [todo-app-complete/](todo-app-complete/) for full workflow.
