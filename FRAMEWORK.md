# Context Mesh - Framework Structure

> 📘 **Complete Reference** - This is the full framework documentation.
> For a quick start, see [GETTING_STARTED.md](GETTING_STARTED.md).

---

## Framework Overview

**The Problem**: AI-generated code works, but context disappears. Three months later, your own code looks foreign.

**The Solution**: Context Mesh makes context the primary artifact. Code becomes its manifestation, not the other way around.

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   INTENT    │ ──► │    BUILD    │ ──► │    LEARN    │
│  What & Why │     │  AI + Human │     │   Update    │
└─────────────┘     └─────────────┘     └─────────────┘
                                               │
                          ◄────────────────────┘
                              Feedback Loop
```

**The 3 Core Steps:**
1. **Intent** - Define what to build and why (create context)
2. **Build** - AI generates code following your context (human supervises)
3. **Learn** - Update context with learnings (refine and improve)

**Why Context Mesh Works:**
- ✅ **Context is primary** - AI understands your architecture and patterns
- ✅ **Decisions preserve full context** - Every choice documented with rationale
- ✅ **Knowledge evolves with your system** - Living context that stays current
- ✅ **Works with any methodology** - Integrates with Scrum, Kanban, DevOps, or your own process
- ✅ **Simple to adopt** - Just 3 steps, similar to Scrum's simplicity

**Context Mesh is not a replacement for Scrum or Agile** - it's a complementary framework specifically designed for AI-First development that can be used alongside existing methodologies.

**Customization**: The 3 steps (Intent, Build, Learn) are fixed, but you can adapt how you execute each step to fit your workflow and team needs.

---

## The 3 Steps

### Step 1: Intent

**Purpose**: Plan and prepare context before building.

| Aspect | Details |
|--------|---------|
| **What it does** | Defines what to build and why, creates feature/bug/refactoring intents, makes technical decisions, creates initial living context |
| **When** | Before building (planning phase) |
| **Outputs** | Intent files (`feature-*.md`, `bug-*.md`), Decision files (`decisions/*.md`), Initial patterns (optional) |
| **Human Role** | Lead intent capture, validate intent clarity, approve initial context |
| **AI Role** | Assist in structuring intent, suggest context organization, generate context from prompts |

**Activities:**
- **Define Intent**: Create `project-intent.md`, `feature-*.md`, `bug-*.md`, or `refactor-*.md`
- **Create Decisions** (recommended): Create `decisions/*.md` files for significant technical choices. Best practice: plan decisions before Build for faster implementation
- **Create Initial Context**: AI can help generate context structure
- **Identify Patterns**: For existing projects, identify existing patterns. For new projects, define initial patterns

**Intent Types:**
- **Initial** (quick start): Basic intent, refine as you learn
- **Refined** (pre-planned): Detailed intent after team discussion

Both approaches are valid.

---

### Step 2: Build

**Purpose**: Construction phase - AI builds code with context, human supervises.

| Aspect | Details |
|--------|---------|
| **What it does** | AI generates code using living context (intent, decisions, patterns), human supervises and validates |
| **When** | After Intent (or during, if iterative) |
| **Prerequisites** | Intent Statement (Required), Technical Decisions/ADR (Required before implementation), Patterns (Optional) |
| **Outputs** | Implemented code, Decision records (if created/updated), Updated context, New patterns (optional) |
| **Human Role** | Supervise AI execution, validate code quality, approve implementation decisions |
| **AI Role** | Explain planning approach, generate code based on context (after approval), suggest solutions |

**Critical Requirement - ADR Before Implementation**: Before implementing any feature, **verify if a technical decision (ADR) exists**. If no decision exists, **create the decision first** in Step 1 (Intent) or at the start of Step 2 (Build) before proceeding. **Do not start implementation without a documented decision**.

**Activities:**
1. **Verify Decision exists** - Check if technical decision exists. If not, create it first
2. **Plan before building** - Load context files, verify ADR is available, ask AI to explain what it will build
3. **Approve before executing** - Review and approve plan, ensure ADR is in place
4. **Execute with context** - AI generates code based on approved plan and documented decisions
5. **Follow patterns** - Use established patterns, avoid known anti-patterns

**Updating Existing Features:**

When updating an existing feature (not creating new):
- **Analyze existing code first** - AI should understand what's already implemented
- **Make incremental changes only** - Modify only what needs to change based on updated intent
- **Preserve existing code** - Don't regenerate code that doesn't need to change
- **Reference "Changes from Original"** - If present in the intent file, follow it explicitly
- **Update related files** - Update tests, documentation, and related code as needed

**Example for AI when updating:**
```
Update the existing feature following @context/intent/feature-[name].md.

IMPORTANT: This is an UPDATE to existing code, not a new implementation.
- First, analyze the existing code for this feature
- Identify what needs to change based on the updated intent
- Make ONLY the necessary modifications
- Preserve existing code that doesn't need to change
```

**Writing Prompts for AI Code Generation:**

Since **context is the primary artifact**, prompts should be **simple and reference the context**.

| Approach | When to Use | Example |
|----------|-------------|---------|
| **✅ Simple Prompts** (Recommended) | Context is sufficient | `Implement authentication following @context/intent/feature-user-auth.md` |
| **✅ AI Agents** (Advanced) | Need structured/reusable execution, working with team | `Execute @context/agents/agent-backend.md for payment feature` |
| **⚠️ Detailed Prompts** (Avoid) | Temporary testing/learning only | Duplicates context, hard to maintain |

**Recommendation**: Start with Simple Prompts (default). Add AI Agents when you need structure or reusability. Avoid Detailed Prompts - use only temporarily, or create an agent file instead.

---

### Step 3: Learn

**Purpose**: Learning phase - Update living context to reflect code changes, document learnings.

| Aspect | Details |
|--------|---------|
| **What it does** | Updates context to reflect actual code changes, documents learnings, updates decisions with outcomes, refines intent if needed |
| **When** | After Build (or continuously during Build) |
| **Outputs** | Updated context, Updated decision records (with outcomes), Updated changelog, Preserved/updated patterns, Learning notes (optional) |
| **Human Role** | Review code changes, decide what needs context updates, validate context accuracy |
| **AI Role** | Explain what changed before updating context, help identify changes, suggest what needs updating, assist in updating documentation |

**Activities:**
1. **Update Context** (Primary): Plan (ask AI to identify what changed), Approve (review AI's analysis), Execute (update context with approval)
2. **Preserve Knowledge**: Preserve patterns identified during Build, update patterns based on learnings, document new anti-patterns
3. **Document Learnings** (Optional): Note what worked well, document challenges or discoveries
4. **Refine Intent** (If needed): Adjust intent based on learnings, create new work items if needed

**Feedback Loop**: Learnings from Step 3 feed back to Step 1 (Intent) for refinement in the next cycle.

---

## Context Structure

Context Mesh uses a simple directory structure to organize context:

```
context/
├── intent/          # Step 1: Intent statements
│   ├── project-intent.md
│   ├── feature-*.md
│   ├── bug-*.md
│   └── refactor-*.md
│
├── decisions/       # Decisions (can be created in any step, recommended in Step 1)
│   └── 001-*.md, 002-*.md, ...
│
├── knowledge/       # Patterns, anti-patterns (all steps)
│   ├── patterns/
│   └── anti-patterns/
│
├── agents/          # Reusable execution patterns (optional)
│   └── agent-*.md
│
└── evolution/       # Step 3: Changelogs, learnings
    ├── changelog.md
    └── learning-*.md
```

**Minimum Viable Context** (start here):
```
context/
├── intent/
│   └── feature-user-auth.md        # What + Why + Acceptance criteria
└── decisions/
    └── 002-auth.md                 # How (technical approach) + Rationale
```

**Full Structure** (add as you grow):
- Patterns and anti-patterns
- Agents for reusable execution
- Evolution tracking (changelog, learnings)

---

## Working with Context Files

### When to Create vs Update

| Situation | Action | Why |
|----------|--------|-----|
| New feature | Create `feature-*.md` | New scope |
| Update existing feature | Update `feature-*.md` | Same scope (Git preserves history) |
| New decision | Create `decisions/003-*.md` | New scope |
| Add outcomes to decision | Update `decisions/002-*.md` | Same scope |
| New pattern discovered | Create `patterns/new-pattern.md` | New scope |
| Refine pattern | Update `patterns/existing-pattern.md` | Same scope |

**Rule of Thumb**: Ask yourself "Is this a new scope or evolution of existing scope?"
- **New scope** → Create new file
- **Same scope** → Update file (Git preserves history)

**Deprecating (NOT Removing)**:
- When a feature is removed → Mark as deprecated, do NOT delete
- When a bug is resolved → Mark as resolved, do NOT delete
- Keep files for history and traceability

### When to Update vs Create New File (Feature Evolution)

**Key Principle**: Use Git for versioning. Update the same file when it's the same feature evolving. Only create a new file when it's a completely different feature.

| Scenario | Action | Example |
|----------|--------|---------|
| **Feature refinement** | Update `feature-*.md` | Adding new fields to user auth, changing UI, adding validation |
| **Feature scope expansion** | Update `feature-*.md` | Adding OAuth to existing auth feature |
| **Technical approach change** | Update `feature-*.md` + Create new decision | Switching from JWT to session-based auth (same feature, different approach) |
| **Complete feature replacement** | Create new `feature-*.md` + Deprecate old | Replacing old auth system with completely new one (different architecture) |
| **Feature split** | Create new `feature-*.md` files | Splitting "user management" into "user-auth.md" and "user-profile.md" |

**How AI Should Handle Feature Updates:**

When you update a feature and execute the agent/prompt, the AI should:
1. **Analyze existing code first** - Understand what's already implemented
2. **Identify what needs to change** - Compare updated intent with current code
3. **Make incremental changes only** - Modify only what's necessary
4. **Preserve existing code** - Don't regenerate code that doesn't need to change
5. **Follow "Changes from Original" section** - If present in the intent file

**Example prompt for AI:**
```
Update the existing feature following @context/intent/feature-[name].md.

IMPORTANT: This is an UPDATE to existing code, not a new implementation.
- First, analyze the existing code for this feature
- Identify what needs to change based on the updated intent
- Make ONLY the necessary modifications
- Preserve existing code that doesn't need to change
```

**How to Document Significant Changes in the Same File:**

When updating a feature file with significant changes, add a "Change History" section:

```markdown
## Change History

### 2024-03-15 - OAuth Integration Added
- **What changed**: Added OAuth (Google, GitHub) to existing email/password auth
- **Why**: User request for social login
- **Impact**: New decision created (005-oauth-integration.md)
- **Status**: Completed

### 2024-02-10 - MFA Added
- **What changed**: Added multi-factor authentication
- **Why**: Security requirement
- **Impact**: Updated decision 002-auth.md with MFA approach
- **Status**: Completed
```

**When to Create a New Feature File:**

Only create a new `feature-*.md` file when:
- It's a **completely different feature** (not an evolution)
- The feature is being **replaced entirely** (then deprecate the old one)
- The feature is being **split into multiple features** (create new files for each)

**Example - When to Update vs Create:**

```
✅ Update feature-user-auth.md:
- Add password reset
- Add email verification
- Add OAuth providers
- Change from JWT to sessions
- Add MFA

❌ Create new file:
- Replacing auth with completely new system → feature-auth-v2.md (deprecate old)
- Splitting auth into separate features → feature-login.md + feature-registration.md
```

**Remember**: Git preserves all history. Updating the same file maintains traceability while keeping context organized. Use Git history to see what changed and when.

### File Naming Conventions

| File Type | Naming Pattern | Example |
|-----------|----------------|---------|
| Project Intent | `project-intent.md` | `project-intent.md` |
| Features | `feature-*.md` | `feature-user-auth.md` |
| Bugs | `bug-*.md` | `bug-login-timeout.md` |
| Refactoring | `refactor-*.md` | `refactor-api-structure.md` |
| Decisions | `001-*.md`, `002-*.md`, ... | `001-tech-stack.md`, `002-auth-approach.md` |
| Patterns | `patterns/*.md` | `patterns/api-design.md` |
| Anti-patterns | `anti-patterns/*.md` | `anti-patterns/avoid-direct-db.md` |
| Evolution | `changelog.md`, `learning-*.md` | `changelog.md`, `learning-auth-refactor.md` |

### Status and Dates

Include at the end of every context file:

```markdown
## Status
- **Created**: YYYY-MM-DD (Phase: Intent/Build/Learn)
- **Status**: [Status Type]
- **Updated**: YYYY-MM-DD (Phase: Intent/Build/Learn) - [reason] (optional)
```

**Status Types:**
- **Intent Files**: Draft, In Progress, Completed, Deprecated, Resolved
- **Decision Files**: Proposed, Accepted, Superseded, Deprecated
- **Knowledge Files**: Active, Deprecated, Superseded
- **Learning Files**: Active, Archived

**Best Practices**: Always include created date, update status when it changes, include phase (which Context Mesh step), be consistent across all files.

### Linking and Traceability

All files should link to related files for full traceability. Include a "Related" section:

```markdown
## Related
- Feature: feature-user-auth.md
- Decision: 002-jwt-authentication.md
- Pattern: jwt-auth-pattern.md
```

This creates traceability: Intent → Decision → Learning → Pattern.

---

## Project Intent vs Features, Bugs, and Refactoring

Understanding when to use `project-intent.md` versus individual feature/bug files:

| File Type | When to Use | When to Update |
|-----------|-------------|---------------|
| **project-intent.md** | Project vision, high-level goals, general scope | Project scope changes significantly, high-level goals change |
| **feature-*.md** | Individual feature requirements | Refining requirements, adding functionality, changing scope |
| **bug-*.md** | Bug description, impact, fix requirements | Refining bug understanding, adding root cause analysis |
| **refactor-*.md** | Refactoring intent, goals, approach | Refining refactoring approach, updating scope |

**Quick Reference:**

| Situation | File to Create/Update | Action |
|----------|----------------------|--------|
| New Feature | `feature-*.md` | Create new file |
| Update Feature | `feature-*.md` (existing) | Update existing file |
| Deprecate Feature | `feature-*.md` (existing) | Mark as deprecated, keep file |
| Bug Fix | `bug-*.md` | Create new file |
| Resolve Bug | `bug-*.md` (existing) | Mark as resolved, keep file |
| Change Project Scope | `project-intent.md` | Update (only for scope changes) |
| Technical Decision | `decisions/*.md` | Create new file |

**Do NOT update `project-intent.md` for**: Adding individual features, fixing bugs, updating existing features, technical decisions.

---

## Decisions, Patterns, and Agents

### Decisions (ADR)

**What**: Technical decisions documented with context, decision, rationale, alternatives, and outcomes.

**When to Create:**
- **Step 1 (Intent) - Recommended**: Plan technical decisions when you know the approach
- **Step 2 (Build) - Flexible**: Create decisions if technical choices emerge during implementation
- **Step 3 (Learn) - Outcomes**: Update decisions with outcomes, create improvement decisions if learnings suggest better approaches

**When to Document:**
- Architectural decisions
- Technology choices
- Design patterns
- Important implementation choices
- Asset management decisions (storage, organization, optimization, external integrations like Figma MCP)

**Format**: Simple markdown with Context, Decision, Rationale, Alternatives, Outcomes.

---

### Patterns & Anti-patterns

**What**: Knowledge that evolves with the system and guides development.

**When Patterns are Established:**

| Step | Activity |
|------|----------|
| **Step 1 (Intent)** | For new projects: Define initial patterns. For existing projects: Identify existing patterns |
| **Step 2 (Build)** | Use established patterns, avoid known anti-patterns, optionally identify new patterns |
| **Step 3 (Learn)** | Preserve patterns identified during Build, update patterns based on learnings, document new anti-patterns |

**Pattern Documentation:**
- **Pattern**: What it is, when to use it, why it works, examples
- **Anti-pattern**: What to avoid, why it's problematic, what problems it causes

Both include context and link to decisions and learnings.

---

### Agents (agent-*.md)

**What**: Simple reusable execution patterns stored in `context/agents/`. They're markdown files that define how to execute specific tasks by referencing Context Mesh files.

**Key principle**: Agents should **reference** context, not duplicate it. All details are in context files - agents just tell AI how to execute.

**When to create an agent:**
- ✅ You find yourself writing the same detailed prompt repeatedly
- ✅ You want to standardize how certain tasks are done
- ✅ You're working with a team and want shared execution patterns
- ✅ You have a complex task that needs structured steps

**Don't create an agent when:**
- ❌ Simple prompts work fine (just reference context files)
- ❌ The task is one-time only
- ❌ Context files already have all the information needed

**Simple Agent Format:**
```markdown
# Agent: [Agent Name]
## Purpose
[What this agent does - one sentence]
## Context Files to Load
- @context/intent/feature-[name].md
- @context/decisions/[number]-[name].md
- @context/knowledge/patterns/[pattern].md
## Execution Steps
1. Load context files listed above
2. [Step 1 - what to do]
3. [Step 2 - what to do]
## Output
- [What this agent produces]
```

**Using agents**: Reference in your prompt: `Execute @context/agents/agent-[name].md for [feature]`.

**Creating agents**: Create manually in `context/agents/` or use the `create-agent.md` prompt (see [prompts/](prompts/)).

For advanced agent patterns, see [ADVANCED.md](ADVANCED.md).

---

## AI-Human Collaboration

**Collaboration Pattern**: **Intent** - Human leads, AI assists | **Build** - AI builds, human supervises | **Learn** - AI analyzes, human validates.

**Plan, Approve, Execute Pattern**: Context Mesh uses this pattern for all AI-assisted work.

1. **Plan** - AI explains what it will do (context creation, code generation, or updates)
2. **Approve** - You review and approve (or request changes), maintain control over execution
3. **Execute** - AI executes only with your approval

**Why it matters**: You maintain control, AI explains before acting, you can refine before execution, reduces rework and improves quality.

**Human Responsibilities**: Lead intent capture and validation, supervise AI execution, review and approve work, validate learnings and insights, make critical decisions.

**AI Responsibilities**: Generate code based on context, suggest solutions and improvements, review code for quality, help identify what needs updating in context, propose context updates.

---

## Definition of Done (DoD)

Context Mesh uses **Definition of Done** at the **technical/feature level only** - criteria that every feature implementation must meet before being considered complete.

**Key Points:**
- **DoD is technical only**: Applied during Step 2 (Build) when code is implemented
- **Steps 1 and 3 don't have DoD**: They have flexible "Outputs" instead, as they are more iterative and adaptive
- **Project-level DoD**: Defined by your team/project, not by Context Mesh. Context Mesh adds the requirement to update context as part of your DoD
- **When to apply**: Only when implementing features (Step 2), not during planning (Step 1) or learning (Step 3)

**Typical DoD Criteria** (for Step 2 - Build):
- Code implemented and working
- Tests passing
- Code review completed
- **Context updated** (Context Mesh requirement)
- Documentation updated
- Deployed (if applicable)

**Acceptance Criteria vs DoD:**
- **Acceptance Criteria** (in `feature-*.md` files) - What the feature needs to do functionally (e.g., "User can login", "Data is saved")
- **Definition of Done** - Process criteria that must be met during implementation (e.g., "Tests passing", "Code reviewed", "Context updated")

---

## Integration & Flexibility

### Integration with Scrum/Agile

Context Mesh can be integrated with Scrum:

| Scrum Event | Context Mesh Step |
|-------------|-------------------|
| Sprint Planning | Step 1 (Intent) for each item |
| During Sprint | Step 2 (Build) |
| Sprint Review | Step 3 (Learn) |
| Retrospective | Step 3 (Learn) - refine context and intent |

Context Mesh adds: Context preservation, AI agent integration, Intent-driven development, Living knowledge evolution, Decision architecture.

### Starting Points

Context Mesh adapts to your needs. Different approaches are equally valid:

| Approach | When to Use | How |
|----------|-------------|-----|
| **Minimal Start** | Exploratory projects, unclear requirements, quick prototypes | Start with basic intent, use AI to expand context, learn as you go |
| **Comprehensive Start** | Large projects, clear requirements, team projects | Include decisions, patterns, DevOps planning in Step 1, create complete context before Build |
| **Existing Projects** | Legacy codebases, taking over projects, refactoring | Use AI to analyze existing code, generate context from codebase, then follow normal workflow |

All approaches are valid - choose based on your needs.

---

## AGENTS.md Integration

Context Mesh works seamlessly with the **[AGENTS.md](https://agents.md/)** standard, an open format used by over 20,000 open-source projects to guide AI coding agents.

**AGENTS.md** acts as a **router** that directs AI agents to Context Mesh files. Keep it **succinct** - it should primarily indicate where to find context, not duplicate it:

- **AGENTS.md** = Operational router (setup commands, workflow, references to Context Mesh files)
- **Context Mesh** = Strategic context (intent, decisions, knowledge, patterns)

**Together**: AGENTS.md routes AI agents to the right Context Mesh files, providing both operational guidance and strategic context.

**Structure**: `AGENTS.md` at project root references `context/` directory. Your `AGENTS.md` should include a "Context Files to Load" section listing relevant context files.

**Important**: AGENTS.md should be **kept updated** to reflect changes in the living context:
- New feature intents → Add to "Feature-Specific Context" section
- New decisions → Add to "Technical Decisions" section
- New patterns → Add to "Knowledge and Patterns" section
- Deprecated features → Update or remove references

**Note**: AGENTS.md is **optional** but **recommended** for better AI agent experience. Context Mesh works perfectly without it, but together they provide complete guidance.

See [TOOLS.md](TOOLS.md) for more details.

---

## Security by Design

Security in Context Mesh is built into the framework from the ground up.

**Security Principles:**
1. **Security by Design**: Security considered at every step
2. **Context Security**: Living Context contains sensitive information - requires access controls, encryption for sensitive context, context classification
3. **Traceability**: All security-relevant actions must be traceable
4. **Least Privilege**: Access to context and systems follows principle of least privilege
5. **Defense in Depth**: Multiple layers of security protection

**Security in Each Step:**
- **Step 1 (Intent)**: Identify security requirements, document security constraints, define security acceptance criteria
- **Step 2 (Build)**: Implement security controls, follow security best practices, document security decisions
- **Step 3 (Learn)**: Monitor security metrics, review security incidents, update security practices

**Security Best Practices**: Start with security from the beginning, document security decisions, regular reviews, keep context secure, monitor continuously in production.

---

## Framework Principles Alignment

Context Mesh implements 5 core principles:

1. **Context as Primary Creation**: Every step creates/updates context
2. **Intent-Driven Architecture**: Architecture flows from intent (Step 1 → Step 2)
3. **Knowledge as Living Entity**: Context evolves continuously (all steps)
4. **Human-AI Collaborative Consciousness**: Clear human-AI roles in each step
5. **Contextual Decision Architecture**: Decisions captured with full context

---

## Next Steps

- **Quick start**: [GETTING_STARTED.md](GETTING_STARTED.md) - Hands-on guide
- **Examples**: [examples/](examples/) - Full working examples
- **Advanced patterns**: [ADVANCED.md](ADVANCED.md) - Advanced agent structures and workflows
- **Integration**: [INTEGRATION.md](INTEGRATION.md) - Use with Scrum/Kanban
- **Tools**: [TOOLS.md](TOOLS.md) - Tool recommendations and AGENTS.md details
- **Questions**: [FAQ.md](FAQ.md) - Common questions

---

**Remember**: Start simple. Add complexity only when needed. Context Mesh adapts to your workflow.
