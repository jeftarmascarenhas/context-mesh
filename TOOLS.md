# Context Mesh Tooling Guide

Context Mesh is designed to be **tool-agnostic** - you can implement it with any tools. This guide provides simple recommendations for getting started.

## Tooling Philosophy

Keep it simple. Context Mesh works best when you start with basic tools and add complexity only when needed.

## Recommended: File-Based Approach

The simplest and most effective way to start with Context Mesh is using file-based context management.

### Tools Needed

- **Markdown files** - For context documentation
- **Git** - For version control
- **Any text editor** - For editing context files
- **AI development tools** (optional) - Cursor, GitHub Copilot, etc.

### Directory Structure

Create a simple directory structure in your project:

```
your-project/
├── AGENTS.md          # Optional: Router for AI agents (references Context Mesh)
├── context/           # Context Mesh: strategic context
│   ├── intent/
│   │   ├── project-intent.md
│   │   ├── feature-*.md
│   │   ├── bug-*.md
│   │   └── refactor-*.md
│   ├── decisions/
│   │   └── 001-*.md, 002-*.md, ...
│   ├── knowledge/
│   │   ├── patterns/
│   │   └── anti-patterns/
│   ├── agents/        # Optional: specialized agent definitions (see ADVANCED.md)
│   │   └── agent-*.md
│   └── evolution/
│       ├── changelog.md
│       └── learning-*.md
└── [your code]
```

### Benefits

- ✅ Simple to set up
- ✅ Version controlled with Git
- ✅ Easy to read and edit
- ✅ No special tools needed
- ✅ Works with any AI tools
- ✅ Portable and shareable

### Getting Started

1. Create the `context/` directory structure
2. Add context files to Git
3. Start documenting intent, decisions, and learnings
4. Use Git for versioning and collaboration

See [GETTING_STARTED.md](GETTING_STARTED.md) for detailed setup instructions.

## Optional: Advanced Tools

As your project grows, you may want to consider:

### Wiki-Based Tools
- **Confluence** - For team collaboration
- **Notion** - For structured documentation
- **GitHub Wiki** - For project documentation

### Documentation Tools
- **MkDocs** - Generate documentation sites
- **Docusaurus** - Documentation framework
- **GitBook** - Documentation platform

### AI Development Tools
- **Cursor** - AI-powered IDE
- **GitHub Copilot** - AI pair programmer
- **Codeium** - AI coding assistant
- **Tabnine** - AI code completion

---

## AGENTS.md Integration

**[AGENTS.md](https://agents.md/)** is an open format used by over 20,000 open-source projects to guide AI coding agents. It works seamlessly with Context Mesh.

### How They Work Together

**AGENTS.md** acts as a **succinct router** that directs AI agents to Context Mesh files. Keep it minimal - the context files contain all the details:

- **AGENTS.md** provides minimal operational instructions:
  - Essential setup commands
  - Basic workflow
  - Code style basics
  - **References to Context Mesh files** (this is the key)

- **Context Mesh** provides all strategic context:
  - Intent (what to build and why)
  - Decisions (how and why we chose)
  - Knowledge (patterns, learnings)

**Together**: AGENTS.md routes AI agents to Context Mesh files, providing operational routing while Context Mesh provides the complete strategic context.

**Important**: AGENTS.md must be **kept updated** to maintain the living context. When context files are added, updated, or removed, update AGENTS.md accordingly to ensure AI agents always have accurate routing to the current context. This keeps the living context synchronized and ensures AI agents can find the right context files.

### Example AGENTS.md Structure

Keep it **succinct** - focus on routing to Context Mesh:

```markdown
# AGENTS.md

## Setup Commands
- Install deps: `pnpm install`
- Start dev server: `pnpm dev`
- Run tests: `pnpm test`

## Code Style
- TypeScript strict mode
- Single quotes, no semicolons

## Context Files to Load

When working on this project, AI agents should load:

- @context/intent/project-intent.md
- @context/decisions/001-tech-stack.md
- @context/decisions/002-database.md
- @context/knowledge/patterns/*.md

## Development Workflow

1. Load Context Mesh files (see above)
2. Follow Context Mesh workflow (Intent → Build → Learn)
3. Update context after changes
```

**Note**: Keep AGENTS.md minimal. All details are in Context Mesh files. Update AGENTS.md when context changes.

### Benefits

- ✅ **Widely Adopted**: Used by 20k+ projects
- ✅ **AI-Friendly**: Designed specifically for AI coding agents
- ✅ **Complementary**: AGENTS.md (operational) + Context Mesh (strategic)
- ✅ **Router Pattern**: AGENTS.md routes to Context Mesh files
- ✅ **Tool Agnostic**: Works with any AI development tool

### When to Use AGENTS.md

**Recommended when**:
- ✅ You want better AI agent experience
- ✅ You have complex setup/build processes
- ✅ You want to document operational instructions
- ✅ You're working with a team

**Optional**: Context Mesh works perfectly without AGENTS.md, but together they provide complete guidance.

### Configuration

Most AI tools automatically detect and use `AGENTS.md`:

- **Cursor**: Automatically loads AGENTS.md
- **Aider**: Configure in `.aider.conf.yml`: `read: AGENTS.md`
- **Gemini CLI**: Configure in `.gemini/settings.json`: `{ "contextFileName": "AGENTS.md" }`

See [AGENTS.md website](https://agents.md/) for more details and examples.

### Example AGENTS.md

See [examples/AGENTS.md.example](examples/AGENTS.md.example) for a complete example of AGENTS.md integrated with Context Mesh.

---

## Best Practices

1. **Start Simple**: Begin with file-based approach
2. **Use Git**: Version control your context
3. **Keep It Simple**: Don't overcomplicate tooling
4. **Add Tools Gradually**: Only add tools when you need them
5. **Tool Agnostic**: Context Mesh works with any tools you prefer

## Further Reading

- [GETTING_STARTED.md](GETTING_STARTED.md) - Getting started guide
- [FRAMEWORK.md](FRAMEWORK.md) - Framework details
- [EXAMPLES.md](EXAMPLES.md) - Real-world examples
