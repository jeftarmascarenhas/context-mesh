# Context Mesh - Advanced Patterns

This document covers advanced patterns and extensions for Context Mesh. These patterns are **optional** and can be adopted as your project grows or when you need more structure.

## Overview

While Context Mesh works perfectly with just the basic 3-step workflow (Intent, Build, Learn), advanced patterns can help with:
- Larger projects with multiple features
- Team collaboration
- Complex build processes
- Reusable execution patterns
- Better organization and scalability

**Important**: These patterns are **extensions**, not requirements. Start simple, add complexity only when needed.

---

## AGENTS.md Integration

**[AGENTS.md](https://agents.md/)** is an open format used by over 20,000 open-source projects. It works seamlessly with Context Mesh as a **router** that uses Context Mesh as the central knowledge hub.

### How AGENTS.md Works with Context Mesh

**AGENTS.md** provides operational instructions (setup, commands, conventions) and **routes** AI agents to Context Mesh files for strategic context (intent, decisions, knowledge).

**Structure**:
```
project/
├── AGENTS.md          # Router: operational instructions + Context Mesh references
├── context/           # Context Mesh: strategic context
│   ├── intent/
│   ├── decisions/
│   └── knowledge/
└── agents/            # Optional: specialized agent definitions (agent-*.md)
    └── agent-*.md
```

**AGENTS.md** should include a section like:
```markdown
## Context Files to Load

When working on this project, AI agents should load:

- @context/intent/project-intent.md
- @context/decisions/001-tech-stack.md
- @context/knowledge/patterns/*.md
```

See [TOOLS.md](TOOLS.md) for complete AGENTS.md integration guide.

**Note**: AGENTS.md is **optional** but **recommended**. It enhances AI agent experience by providing operational guidance while Context Mesh provides strategic context.

---

## AI Agents Structure (agent-*.md)

### What are AI Agents?

AI Agents are structured definitions that specify how AI should execute specific parts of the Build phase. They complement the Context Mesh by providing **execution patterns** alongside the **context** (intent, decisions, patterns).

**Relationship**:
- **Context Mesh** = What and why (intent, decisions, knowledge)
- **AI Agents** = How to execute (build automation, execution patterns)

### When to Use AI Agents

**Use AI Agents (agent-*.md) when**:
- ✅ You have complex build processes
- ✅ You want to modularize execution
- ✅ You need reusable execution patterns
- ✅ You're working with a team
- ✅ You want to execute specific parts of the build
- ✅ You find yourself writing detailed prompts repeatedly

**Don't use AI Agents when**:
- ❌ Your project is simple (use simple prompts instead)
- ❌ You're just starting (start with simple prompts)
- ❌ You prefer ad-hoc execution
- ❌ Context alone is sufficient (simple prompts work)

### AI Agents vs Simple Prompts vs Detailed Prompts

**Hierarchy of Approaches**:

1. **✅ Simple Prompts** (Recommended - Default)
   - Use when: Context is sufficient
   - Example: `"Implement authentication following @context/intent/feature-user-auth.md"`
   - Start here for all projects

2. **✅ AI Agents (agent-*.md)** (Advanced - When Needed)
   - Use when: Need structured/reusable execution, teams, complex projects
   - Example: `"Execute @agents/agent-backend.md for payment feature"`
   - Add when simple prompts aren't enough

3. **⚠️ Detailed Prompts** (Avoid - Temporary Only)
   - Use when: Testing, temporary override, learning
   - Not recommended: Duplicates context, hard to maintain
   - If needed frequently, create an agent file instead

**Decision Guide**:
- **Simple project, single feature** → Use **Simple Prompts**
- **Complex project, multiple features** → Use **AI Agents**
- **Team collaboration** → Use **AI Agents**
- **Temporary test** → **Detailed Prompt** (acceptable, but temporary)
- **Learning** → Start with **Simple Prompts**

**Key Principle**: If you're writing detailed prompts repeatedly, create an `agent-*.md` file instead. This makes the pattern reusable and structured.

### Structure

Create an `agents/` directory alongside your `context/` directory and `AGENTS.md`:

```
project/
├── AGENTS.md          # Router: operational instructions + Context Mesh references
├── context/           # Context Mesh (what and why)
│   ├── intent/
│   ├── decisions/
│   └── knowledge/
│
└── agents/            # Specialized AI Agents (how to execute specific parts)
    ├── agent-planner.md
    ├── agent-developer.md
    ├── agent-reviewer.md
    ├── agent-devops.md
    └── agent-insights.md
```

**Relationship**:
- **AGENTS.md** = Router that references Context Mesh (operational + routing)
- **agent-*.md** = Specialized execution patterns (modular workflows)
- **Context Mesh** = Strategic context (intent, decisions, knowledge)

### Agent File Format

Each agent file follows this structure. You can use a **simple format** for basic agents or a **detailed format** for specialized agents:

#### Simple Format (Basic Agents)

```markdown
# Agent: [Agent Name]

## Purpose
[What this agent does]

## Responsibilities
- [Responsibility 1]
- [Responsibility 2]
- [Responsibility 3]

## Context Files to Load
- @context/intent/[relevant-intent].md
- @context/decisions/[relevant-decision].md
- @context/knowledge/patterns/[relevant-pattern].md

## Execution Steps
1. [Step 1]
2. [Step 2]
3. [Step 3]

## Scope
- [What this agent can do]
- [What this agent cannot do]

## Outputs
- [Output 1]
- [Output 2]

## Related
- Intent: [related-intent].md
- Decision: [related-decision].md
- Other Agents: [related-agents].md
```

#### Detailed Format (Specialized Agents)

For specialized agents (backend, frontend, database, etc.), use a more detailed format:

```markdown
# Agent: [Agent Name] — [Specialization]

## Scope
- **Allowed directories:** [specific paths]
- **Must read:** [required context files]
- **Prohibited:** [what this agent cannot change]

## Responsibilities
- [Specific technical responsibility 1]
- [Specific technical responsibility 2]
- [Specific technical responsibility 3]

## Conventions
- [Code convention 1]
- [Code convention 2]
- [Architecture pattern to follow]

## Definition of Done (DoD)
- [DoD criterion 1]
- [DoD criterion 2]
- [DoD criterion 3]

## Example Tasks
- "Task example 1"
- "Task example 2"

## References
- @context/decisions/[relevant-decision].md
- @context/knowledge/patterns/[relevant-pattern].md
- [Other relevant files]
```

**Choose the format based on your needs:**
- **Simple format**: For general-purpose agents (Planner, Developer, Reviewer) or when starting out
- **Detailed format**: For specialized agents (Backend, Frontend, Database, specific features) or when you need strict boundaries and conventions

**Key differences:**
- **Simple format**: Flexible, general-purpose, good for learning
- **Detailed format**: Strict scope, technical conventions, DoD, better for production teams

---

## Standard AI Agents

Context Mesh defines five standard agent types based on the framework's AI Agent roles:

### 1. Planner Agent

**Purpose**: Assists in planning and backlog creation during Step 1 (Intent).

**Responsibilities**:
- Analyze requirements and create structured intents
- Suggest feature breakdown
- Help create decisions when approach is known
- Organize context structure

**Example** (`agents/agent-planner.md`):
```markdown
# Agent: Planner

## Purpose
Assist in planning and creating structured context during Step 1 (Intent).

## Responsibilities
- Analyze requirements and create intent statements
- Suggest feature breakdown and organization
- Help create technical decisions when approach is known
- Organize context structure

## Context Files to Load
- @context/intent/project-intent.md (if exists)
- @context/knowledge/patterns/*.md (for reference)

## Execution Steps
1. Analyze requirements or user input
2. Create or refine intent statements
3. Suggest feature breakdown
4. Help create decisions if technical approach is known
5. Organize context structure

## Scope
- Can create intent files
- Can suggest decisions
- Can organize context
- Cannot execute code generation

## Outputs
- Intent statements (feature-*.md, bug-*.md)
- Suggested decisions (decisions/*.md)
- Context organization suggestions

## Related
- Framework Step: Step 1 (Intent)
- Other Agents: agent-developer.md (uses output from Planner)
```

### 2. Developer Agent

**Purpose**: Generates code based on context during Step 2 (Build).

**Responsibilities**:
- Read context files (intent, decisions, patterns)
- Generate code following established patterns
- Link code to context
- Update context with implementation details

**Example** (`agents/agent-developer.md`):
```markdown
# Agent: Developer

## Purpose
Generate code based on context, following patterns and decisions during Step 2 (Build).

## Responsibilities
- Read context files (intent, decisions, patterns)
- Generate code following established patterns
- Avoid known anti-patterns
- Link code to context
- Update context with implementation details

## Context Files to Load
- @context/intent/feature-*.md (or bug-*.md, refactor-*.md)
- @context/intent/project-intent.md (for overall context)
- @context/decisions/*.md (relevant decisions)
- @context/knowledge/patterns/*.md (relevant patterns)
- @context/knowledge/anti-patterns/*.md (to avoid)

## Execution Steps
1. Load relevant context files
2. Understand intent and decisions
3. Review patterns to follow
4. Review anti-patterns to avoid
5. Generate code following patterns
6. Link code to context (comments, documentation)
7. Update context with implementation details if needed

## Scope
- Can generate complete features
- Can generate specific components
- Can update existing code
- Can create new decisions if technical choices emerge
- Cannot deploy (use agent-devops.md)

## Outputs
- Generated code
- Code-context links
- Updated context (if implementation differs from plan)
- New decisions (if created during Build)

## Related
- Framework Step: Step 2 (Build)
- Other Agents: agent-reviewer.md (reviews output), agent-devops.md (deploys)
```

### 3. Reviewer Agent

**Purpose**: Reviews code for quality and context alignment during Step 2 (Build).

**Responsibilities**:
- Review code quality
- Validate against intent
- Check pattern compliance
- Identify anti-patterns
- Suggest improvements

**Example** (`agents/agent-reviewer.md`):
```markdown
# Agent: Reviewer

## Purpose
Review code for quality and context alignment during Step 2 (Build).

## Responsibilities
- Review code quality
- Validate code against intent
- Check pattern compliance
- Identify anti-patterns
- Suggest improvements

## Context Files to Load
- @context/intent/feature-*.md (to validate against)
- @context/decisions/*.md (to check compliance)
- @context/knowledge/patterns/*.md (to validate patterns)
- @context/knowledge/anti-patterns/*.md (to identify issues)

## Execution Steps
1. Load code to review
2. Load relevant context files
3. Validate code against intent
4. Check pattern compliance
5. Identify anti-patterns
6. Review code quality
7. Suggest improvements

## Scope
- Can review code
- Can suggest improvements
- Can identify issues
- Cannot fix code (use agent-developer.md)

## Outputs
- Review report
- Quality assessment
- Improvement suggestions
- Anti-pattern identification

## Related
- Framework Step: Step 2 (Build)
- Other Agents: agent-developer.md (generates code to review)
```

### 4. DevOps Agent

**Purpose**: Manages deployment and observability during Step 3 (Learn).

**Responsibilities**:
- Manage deployment
- Configure observability
- Ensure deployment traceability
- Link deployment to context

**Example** (`agents/agent-devops.md`):
```markdown
# Agent: DevOps

## Purpose
Manage deployment, configure observability, and ensure deployment traceability during Step 3 (Learn).

## Responsibilities
- Manage deployment process
- Configure observability
- Ensure deployment traceability
- Link deployment to context

## Context Files to Load
- @context/intent/feature-*.md (to understand what's being deployed)
- @context/decisions/*.md (to understand deployment decisions)
- @context/evolution/changelog.md (to update)

## Execution Steps
1. Load relevant context files
2. Understand what's being deployed
3. Execute deployment
4. Configure observability
5. Update changelog
6. Link deployment to context

## Scope
- Can manage deployment
- Can configure observability
- Can update changelog
- Cannot generate code (use agent-developer.md)

## Outputs
- Deployment status
- Observability configuration
- Updated changelog
- Deployment-context links

## Related
- Framework Step: Step 3 (Learn)
- Other Agents: agent-developer.md (generates code to deploy), agent-insights.md (analyzes metrics)
```

### 5. Insights Agent

**Purpose**: Analyzes metrics and extracts learnings during Step 3 (Learn).

**Responsibilities**:
- Analyze metrics and observability data
- Extract learnings
- Update context with outcomes
- Suggest intent refinements

**Example** (`agents/agent-insights.md`):
```markdown
# Agent: Insights

## Purpose
Analyze metrics, extract learnings, and update context during Step 3 (Learn).

## Responsibilities
- Analyze metrics and observability data
- Extract learnings from results
- Update context with outcomes
- Suggest intent refinements

## Context Files to Load
- @context/intent/feature-*.md (to understand what was built)
- @context/decisions/*.md (to update with outcomes)
- @context/evolution/changelog.md (to understand changes)

## Execution Steps
1. Load relevant context files
2. Analyze metrics and observability data
3. Extract learnings
4. Update decision records with outcomes
5. Update context to reflect actual implementation
6. Suggest intent refinements if needed

## Scope
- Can analyze metrics
- Can extract learnings
- Can update context
- Can suggest improvements
- Cannot deploy (use agent-devops.md)

## Outputs
- Learning notes
- Updated decision records (with outcomes)
- Updated context
- Intent refinement suggestions

## Related
- Framework Step: Step 3 (Learn)
- Other Agents: agent-devops.md (provides metrics), agent-planner.md (uses learnings for next cycle)
```

---

## Using AI Agents

### Basic Workflow

1. **Step 1 (Intent)**: Use `agent-planner.md` to help structure intent
2. **Step 2 (Build)**: Use `agent-developer.md` to generate code, `agent-reviewer.md` to review
3. **Step 3 (Learn)**: Use `agent-devops.md` to deploy, `agent-insights.md` to learn

### Execution Patterns

**Pattern 1: Complete Build**
```
1. Load: @agents/agent-developer.md
2. Load: @context/intent/feature-*.md
3. Load: @context/decisions/*.md
4. Execute: "Generate the feature following the Developer agent instructions"
```

**Pattern 2: Modular Execution with Specialized Agents**
```
1. Load: @agents/agent-backend.md (specialized agent)
2. Load: @context/intent/feature-*.md
3. Load: @context/decisions/002-database.md
4. Execute: "Generate the backend API following agent-backend.md instructions"
5. Then: Load @agents/agent-reviewer.md and review
```

**Pattern 2b: Feature-Specific Agent**
```
1. Load: @agents/agent-payment.md (feature-specific agent)
2. Load: @context/intent/feature-payment.md
3. Execute: "Implement payment feature following agent-payment.md"
```

**Pattern 3: Full Workflow**
```
1. Intent: Use agent-planner.md
2. Build: Use agent-developer.md + agent-reviewer.md
3. Learn: Use agent-devops.md + agent-insights.md
```

### Custom Agents

You can create custom agents for specific needs. Here are examples of specialized agents:

#### Example 1: Backend Specialist (Detailed Format)

**Example**: `agent-backend.md`
```markdown
# Agent: Backend Specialist (NestJS + Prisma)

## Scope
- **Allowed directories:** `/apps/api/src/**`, `/apps/api/prisma/**`
- **Must read:** `AGENTS.md`, `context/decisions/001-tech-stack.md`, `context/decisions/002-database.md`, `context/intent/project-intent.md`
- **Prohibited:** Changes to `package.json` at root, Docker files, or repo structure **without explicit instruction**.

## Responsibilities
- Scaffold NestJS modules: `controller`, `service`, `dto` (no business logic in controllers)
- Implement Prisma models & **migrations**; update **seeds** when applicable
- Add **Swagger** decorators and tag routes by module
- Enforce **tenant scoping** on all queries (see decision 002-database.md)
- Implement **Auth** per decision 005-auth.md (GitHub OAuth + Email/Password; JWT guards)
- Integrate **BullMQ stubs** for Orchestrator/Observer registration (runtime module)

## Conventions
- Place modules under: `apps/api/src/modules/<feature>/`
- DTOs go in `dto/` with `class-validator` + `class-transformer`
- Export services via module providers; **avoid** cross-service direct imports
- Use **PrismaService** via DI; no raw SQL unless justified in comments
- Add **unit tests (Jest)** under `__tests__/` in each module

## Definition of Done (DoD)
- Prisma model + migration applied
- DTOs with validation + Swagger documented
- Service with business logic; controller thin
- Unit tests passing; lints passing
- Tenant filters in queries; no secrets logged
- Endpoints appear in Swagger `/api/docs`

## Example Tasks
- "Add CRUD for **Network** (decision 002-database.md), including unique `(tenantId, chainId)` constraint"
- "Implement **Auth** module per decision 005-auth.md with JWT guard + `@CurrentUser()` decorator"
- "Create **Contract** module: store ABI JSONB and validate functions on create"

## References
- @context/decisions/001-tech-stack.md
- @context/decisions/002-database.md
- @context/decisions/005-auth.md
- @context/knowledge/patterns/nestjs-module-pattern.md
```

#### Example 2: Frontend Specialist

**Example**: `agent-frontend.md`
```markdown
# Agent: Frontend Specialist (React + TypeScript)

## Scope
- **Allowed directories:** `/apps/web/src/**`, `/apps/web/public/**`
- **Must read:** `context/decisions/001-tech-stack.md`, `context/intent/feature-*.md`
- **Prohibited:** Changes to build configuration, root package.json **without explicit instruction**.

## Responsibilities
- Create React components following design system
- Implement TypeScript types/interfaces
- Add form validation
- Implement API integration
- Add unit tests (React Testing Library)

## Conventions
- Components in `components/` directory
- Pages in `pages/` directory
- Hooks in `hooks/` directory
- Types in `types/` directory
- Use design system components (see decision 003-ui-framework.md)

## Definition of Done (DoD)
- Components follow design system
- TypeScript types defined
- Form validation implemented
- API integration working
- Unit tests passing
- Responsive design verified

## Example Tasks
- "Create login page with form validation"
- "Implement user profile component"
- "Add API integration for feature X"

## References
- @context/decisions/001-tech-stack.md
- @context/decisions/003-ui-framework.md
- @context/intent/feature-*.md
```

#### Example 3: Database Specialist

**Example**: `agent-database.md`
```markdown
# Agent: Database Specialist (Prisma)

## Scope
- **Allowed directories:** `/prisma/**`
- **Must read:** `context/decisions/002-database.md`, `context/intent/feature-*.md`
- **Prohibited:** Direct database changes, raw SQL migrations **without explicit instruction**.

## Responsibilities
- Design Prisma schema models
- Create migrations
- Update seeds
- Ensure data integrity constraints
- Optimize queries

## Conventions
- Models follow naming convention (see decision 002-database.md)
- Migrations are reversible
- Seeds are idempotent
- Indexes for performance-critical queries

## Definition of Done (DoD)
- Prisma schema updated
- Migration created and tested
- Seeds updated if needed
- Constraints validated
- Performance indexes added

## Example Tasks
- "Add User model with email unique constraint"
- "Create migration for Network table"
- "Add indexes for tenant queries"

## References
- @context/decisions/002-database.md
- @context/intent/feature-*.md
```

#### Example 4: Feature-Specific Agent

**Example**: `agent-payment.md`
```markdown
# Agent: Payment Feature Specialist

## Scope
- **Allowed directories:** `/apps/api/src/modules/payment/**`, `/apps/web/src/features/payment/**`
- **Must read:** `context/intent/feature-payment.md`, `context/decisions/004-payment-provider.md`
- **Prohibited:** Changes outside payment module **without explicit instruction**.

## Responsibilities
- Implement payment processing backend
- Create payment UI components
- Integrate with payment provider (Stripe)
- Handle webhooks
- Implement payment status tracking

## Conventions
- Follow payment provider patterns (see decision 004-payment-provider.md)
- Secure payment data handling
- Webhook idempotency

## Definition of Done (DoD)
- Payment flow end-to-end working
- Webhook handling implemented
- Payment status tracking
- Error handling complete
- Tests passing

## Example Tasks
- "Implement Stripe payment integration"
- "Create payment confirmation page"
- "Add webhook handler for payment events"

## References
- @context/intent/feature-payment.md
- @context/decisions/004-payment-provider.md
- @context/knowledge/patterns/payment-flow.md
```

---

## Adapting Existing Agents to Context Mesh

If you already have agents defined (like the NestJS + Prisma example) or use AGENTS.md, adapt them to Context Mesh:

### AGENTS.md Integration

**AGENTS.md** works as a router that references Context Mesh files. Update your `AGENTS.md` to reference Context Mesh:

**Before (Without Context Mesh)**:
```markdown
## Must read: `AGENTS.md`, ADR-000..ADR-005, `MVP_OVERVIEW.md`
```

**After (With Context Mesh)**:
```markdown
## Context Files to Load

When working on this project, AI agents should load:

- @context/intent/project-intent.md (overall project goals)
- @context/decisions/001-tech-stack.md (was ADR-000)
- @context/decisions/002-database.md (was ADR-002)
- @context/decisions/005-auth.md (was ADR-005)
- @context/knowledge/patterns/nestjs-module-pattern.md
```

### Agent Files (agent-*.md) Integration

**Before (Without Context Mesh)**:
```markdown
## Must read: `AGENTS.md`, ADR-000..ADR-005, `MVP_OVERVIEW.md`
```

**After (With Context Mesh)**:
```markdown
## Must read: 
- @context/intent/project-intent.md
- @context/decisions/001-tech-stack.md (was ADR-000)
- @context/decisions/002-database.md (was ADR-002)
- @context/decisions/005-auth.md (was ADR-005)
- @context/knowledge/patterns/nestjs-module-pattern.md
```

### Migration Steps

1. **Update AGENTS.md**: Add "Context Files to Load" section referencing Context Mesh files
2. **Map ADRs to Decisions**: Convert `ADR-XXX` references to `context/decisions/XXX-*.md`
3. **Map Overview to Intent**: Convert `MVP_OVERVIEW.md` to `context/intent/project-intent.md`
4. **Add Pattern References**: Link to `context/knowledge/patterns/` when applicable
5. **Update Agent Files**: Update `agents/agent-*.md` files to reference Context Mesh
6. **Update References Section**: Use Context Mesh file references (`@context/...`)

### Benefits of Migration
- ✅ Better organization (all context in one place)
- ✅ Full traceability (intent → decisions → code)
- ✅ Living context (updates with learnings)
- ✅ Framework consistency

## Best Practices

### 1. Start Simple
- Don't create agents until you need them
- Start with basic Context Mesh
- Add agents when complexity grows
- Use simple format first, detailed format when needed

### 2. Keep Agents Focused
- Each agent should have a clear, single purpose
- Don't mix responsibilities
- Keep scope well-defined
- Use detailed format for strict boundaries

### 3. Link to Context
- Always link agents to relevant context files
- Use `@context/...` references
- Update context when agents execute
- Maintain traceability

### 4. Document Execution
- Document how to use each agent
- Include example tasks
- Keep agents updated
- Add DoD for specialized agents

### 5. Reuse and Share
- Reuse agents across projects
- Share agents with team
- Create agent library
- Adapt existing agents to Context Mesh structure

### 6. Choose the Right Format
- **Simple format**: General-purpose, learning, small projects
- **Detailed format**: Specialized, production, strict boundaries, team collaboration

---

## Integration with Context Mesh

AI Agents **complement** Context Mesh, they don't replace it:

**Context Mesh provides**:
- Intent (what and why)
- Decisions (how and why)
- Knowledge (patterns, anti-patterns)
- Learnings (what we learned)

**AI Agents provide**:
- Execution patterns (how to execute)
- Modular workflows
- Reusable automation
- Team collaboration patterns

**Together**:
- Context Mesh = Foundation (what, why, how decided)
- AI Agents = Execution (how to execute)
- Result = Complete AI-First workflow

---

## Examples

### Example 1: Simple Feature

**Without Agents** (basic Context Mesh):
```
1. Load: @context/intent/feature-auth.md
2. Load: @context/decisions/001-jwt.md
3. Prompt: "Generate authentication feature"
```

**With Agents**:
```
1. Load: @agents/agent-developer.md
2. Load: @context/intent/feature-auth.md
3. Load: @context/decisions/001-jwt.md
4. Prompt: "Execute Developer agent for authentication feature"
```

### Example 2: Complex Feature

**With Agents** (modular):
```
1. Load: @agents/agent-developer.md
2. Load: @context/intent/feature-checkout.md
3. Execute: "Generate API layer only"
4. Then: Load @agents/agent-reviewer.md
5. Execute: "Review API layer"
6. Then: Continue with UI layer...
```

---

## When Not to Use Agents

Don't use agents when:
- ❌ Your project is simple (basic Context Mesh is enough)
- ❌ You're just starting (keep it simple)
- ❌ You prefer ad-hoc execution
- ❌ Agents add more complexity than value

**Remember**: Agents are **optional extensions**. Use them when they add value, not because they exist.

---

## Further Reading

- [FRAMEWORK.md](FRAMEWORK.md) - Core framework structure
- [PRINCIPLES.md](PRINCIPLES.md) - AI-First principles (includes AI Agent roles)
- [GETTING_STARTED.md](GETTING_STARTED.md) - Getting started guide
- [EXAMPLES.md](EXAMPLES.md) - Real-world examples

---

## Summary

AI Agents are an **advanced pattern** that extends Context Mesh with structured execution patterns. They're useful for:
- Larger projects
- Team collaboration
- Complex build processes
- Reusable execution patterns

**Key Points**:
- ✅ Optional extension (not required)
- ✅ Complements Context Mesh
- ✅ Provides execution patterns
- ✅ Start simple, add when needed
- ✅ Keep agents focused and documented

Start with basic Context Mesh, add agents when complexity grows.

