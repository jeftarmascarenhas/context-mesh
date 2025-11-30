# Context Mesh - Framework Structure

## Framework Overview

Context Mesh is an AI-First development framework that implements the 5 Philosophical Principles of AI-First Development. Context Mesh treats context as the primary creation, with code as its manifestation, enabling sustainable AI-assisted development.

**Context Mesh is not a replacement for Scrum or Agile** - it's a complementary framework specifically designed for AI-First development that can be used alongside existing methodologies.

## Using AI as Your Assistant

Context Mesh works with AI tools (Cursor, GitHub Copilot, etc.) as assistants:

- **Step 1 (Intent)**: Use AI to help structure and refine your intent
- **Step 2 (Build)**: Use AI to generate code based on your context
- **Step 3 (Learn)**: Use AI to help identify changes and update context

You maintain control - AI assists, you decide.

## Definition of Done (DoD)

Each step in Context Mesh has a **Definition of Done** - a clear checklist that ensures the step is complete and context is preserved.

**Why DoD matters:**
- Ensures context is never lost
- Makes it clear when a step is complete
- Helps maintain quality and consistency
- Enables team alignment

**The 3 Core Artifacts:**
1. **Intent** - What and why (Step 1)
2. **Decisions** - How and why we chose (Step 2)
3. **Learnings** - What we learned (Step 3)

Each step's DoD ensures these artifacts are created and maintained.

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
├── decisions/       # Step 2: Decision records
│   └── 001-*.md, 002-*.md, ...
│
├── knowledge/       # Patterns, anti-patterns (all steps)
│   ├── patterns/
│   └── anti-patterns/
│
└── evolution/       # Step 3: Changelogs, learnings
    ├── changelog.md
    └── learning-*.md
```

**Why this structure:**
- Simple and clear organization
- Easy to navigate and maintain
- Works with any tools (or no tools)
- Flexible - add subdirectories as needed

## The 3-Step Context Mesh Workflow

Context Mesh is designed for simplicity and easy adoption, similar to Scrum. The framework consists of three essential steps that preserve context throughout the development lifecycle:

```
┌─────────────┐
│   INTENT    │ ← Define intent + create living context
└──────┬──────┘
       │
       ↓
┌─────────────┐
│    BUILD    │ ← AI builds + human supervises + context evolves
└──────┬──────┘
       │
       ↓
┌─────────────┐
│    LEARN    │ ← Learn + update context + refine intent
└──────┬──────┘
       │
       └──────→ (feedback loop)
                └──────→ INTENT (refined)
```

---

### Step 1: Intent

**Purpose**: Capture intent and initialize living context.

**What it does**: 
- Defines what you want to build and why
- Creates initial living context
- Identifies or defines initial patterns (for existing/new projects)

**Intent can be:**
- **Initial** (quick start): Basic intent, refine as you learn
- **Refined** (pre-planned): Detailed intent after team discussion

**Both approaches are valid** - choose based on your project needs.

**Activities**:
- Define intent (what and why)
- Optionally refine intent (team discussion, stakeholder alignment)
- Create initial context
- Identify or define initial patterns:
  - **For existing projects**: Identify existing patterns in codebase
  - **For new projects**: Define initial patterns based on team experience
- Align stakeholders

**Human Role**:
- Lead intent capture
- Validate intent clarity
- Approve initial context

**AI Role**:
- Assist in structuring intent
- Suggest context organization
- Analyze similar projects for insights

**Outputs**:
- Clear Intent Statement
- Initial Living Context
- Initial Patterns (if identified or defined)

**Definition of Done**:
- [ ] Intent statement is clear and validated (What + Why) - **Required**
- [ ] Initial context created and stored
- [ ] Initial patterns identified (existing projects) or defined (new projects) - **Optional**
- [ ] Stakeholders aligned on intent

**Principles Applied**:
- ✅ **Context as Primary Creation** - Context is created first
- ✅ **Intent-Driven Architecture** - Intent guides everything

---

### Step 2: Build

**Purpose**: AI builds with context, human supervises, and decisions are documented.

**Prerequisites** (from Step 1):
- ✅ Intent Statement (What + Why) - **Required**
- ✅ Initial patterns (if known) - **Optional, can identify during Build**
- ✅ Intent decisions (if made) - **Optional**

**Note**: Decisions can be created in any step:
- **Step 1**: Intent decisions (approach, strategy) - Optional
- **Step 2**: Implementation decisions (technical) - Most common
- **Step 3**: Improvement decisions (refinements) - Optional

Decisions are **not required before starting Build**, but may exist if created in Step 1.

**What it does**:
- AI generates code using living context (including patterns/anti-patterns)
- Human supervises and validates
- Decisions are documented in context
- Context is continuously updated
- Follows established patterns, avoids known anti-patterns

**Activities**:
- AI generates code based on context (intent, existing decisions/patterns if any)
- Human supervises and validates AI work
- Document implementation decisions (created during Build, or use existing from Step 1)
- Follow established patterns from knowledge/ (if available)
- Avoid known anti-patterns from knowledge/ (if available)
- Identify new patterns during implementation (optional)
- Update context continuously
- Review code quality
- Validate against intent

**Context Artifacts**:
- Implementation Code (with context links)
- Decision Records (why decisions were made)
- Build Context Updates
- Code-Context Mapping

**Human Role**:
- Supervise AI execution
- Validate code quality
- Approve implementation decisions
- Review context updates
- Make critical decisions

**AI Role**:
- Generate code based on context
- Suggest technical solutions
- Review code for context alignment
- Propose improvements

**Outputs**:
- Implemented Code (context-linked)
- Decision Records
- Updated Living Context
- Implementation Documentation
- New Patterns Identified (optional)

**Definition of Done**:
- [ ] Code implemented using context
- [ ] Important decisions documented (with rationale)
- [ ] Code linked to context (intent, decisions)
- [ ] Human review completed
- [ ] Context updated with implementation details
- [ ] Code validated against intent

**Principles Applied**:
- ✅ **Human-AI Collaborative Consciousness** - Explicit collaboration
- ✅ **Contextual Decision Architecture** - Decisions with context
- ✅ **Knowledge as Living Entity** - Context evolves continuously

---

### Step 3: Learn

**Purpose**: Update living context to reflect code changes.

**What it does**:
- Updates context to reflect actual code changes
- Documents learnings from development process
- Refines intent if needed
- Creates feedback loop to Intent

**Activities**:
1. **Update Context** (Primary):
   - Review code changes
   - Use AI to help identify what changed
   - Update context to match current codebase
   - Update decision records if implementation differed
   - Update changelog with significant changes

2. **Preserve Knowledge** (Important):
   - Preserve patterns identified during Build
   - Update patterns based on learnings
   - Document new anti-patterns discovered
   - Preserve context around patterns/anti-patterns

3. **Document Learnings** (Optional):
   - Note what worked well
   - Document challenges or discoveries

4. **Refine Intent** (If needed):
   - Adjust intent based on learnings
   - Create new work items if needed

**Context Artifacts**:
- Updated Context (reflecting code changes)
- Updated Decision Records (if outcomes differ)
- Changelog entries (documenting what changed)
- Learning Notes (optional)
- Preserved Patterns (if identified during Build)
- Refined Intent (if needed)

**Human Role**:
- Review code changes
- Decide what needs context updates
- Update context (with AI assistance)
- Validate context accuracy

**AI Role**:
- Help identify what changed in code
- Suggest what needs updating in context
- Assist in updating documentation

**Outputs**:
- Updated Living Context
- Updated Decision Records (if applicable)
- Updated Changelog
- Preserved/Updated Patterns (if applicable)
- Learning Notes (optional)
- Refined Intent (if needed)

**Definition of Done**:
- [ ] Context updated to reflect code changes
- [ ] Context aligned with current codebase
- [ ] Changelog updated with significant changes
- [ ] Patterns preserved/updated in knowledge/ (if applicable)
- [ ] Decision records updated if outcomes differ (optional)
- [ ] Learnings documented (optional)
- [ ] Intent refined if needed (optional)

**Principles Applied**:
- ✅ **Knowledge as Living Entity** - Knowledge evolves
- ✅ **Context as Primary Creation** - Context is updated
- ✅ **Intent-Driven Architecture** - Intent is refined

---

## Feedback Loop

### Primary Feedback Loop: Learn → Intent

**Mechanism**: Insights from Step 3 (Learn) feed directly back to Step 1 (Intent)

**Refinement happens:**
- **Before Step 1**: Team refines intent before starting (optional)
- **After Step 3**: Refine intent based on learnings (feedback loop)
- **Result**: Refined intent feeds back to Step 1 for next cycle

**Flow**:
1. Learnings from results → Intent refinement
2. Outcome analysis → Intent refinement
3. Context evolution → Enhanced intent
4. Updated decisions → Better future decisions
5. Patterns preserved → Better future implementations

**Context Updates**:
- Living context automatically evolves
- Intent statements refined
- Decision records updated with outcomes
- Patterns updated with learnings
- Changelog updated
- New work items created from learnings

---

## Living Context

Living Context is the central knowledge repository that:

- **Stores**: Intent, decisions, implementation details, learnings, patterns, anti-patterns
- **Evolves**: Continuously updates as system changes
- **Traces**: Full traceability from intent to code to outcomes
- **Connects**: Links intent → decisions → code → learnings
- **Preserves**: Patterns and anti-patterns with their context

**Key Characteristics**:
- Always up-to-date
- Versioned (using Git or similar)
- Searchable and queryable
- Linked relationships between artifacts

**How to Maintain**:
- Update context during Build step
- Update context during Learn step
- Keep context simple and focused
- Link everything to intent
- Preserve patterns and anti-patterns in knowledge/

---

## Patterns & Anti-patterns

Patterns and anti-patterns are knowledge that evolves with the system and guide development.

**When Patterns are Established**:

**For New Projects** (Step 1: Intent):
- Define initial patterns based on team experience or best practices
- Start with minimal set, evolve as you learn

**For Existing Projects** (Step 1: Intent):
- Identify existing patterns in the codebase
- Document patterns that are working well
- Identify anti-patterns that should be avoided

**During Build** (Step 2):
- Use established patterns from knowledge/
- Follow patterns when implementing
- Avoid known anti-patterns
- Optionally identify new patterns during implementation

**During Learn** (Step 3):
- Preserve patterns identified during Build
- Update patterns based on learnings
- Document new anti-patterns discovered
- Refine pattern context based on outcomes

**Pattern Documentation**:
- **Pattern**: What it is, when to use it, why it works, examples
- **Anti-pattern**: What to avoid, why it's problematic, what problems it causes
- Both include context and link to decisions and learnings

---

## Context File Organization

### File Creation Rules

**Create New File:**
- New work item (feature, bug, refactoring) → new intent file
- New significant decision → new decision file
- New pattern/anti-pattern → new knowledge file
- Important learning → new learning file

**Update Existing File:**
- Refine intent → update or create refined version
- Add outcomes to decision → update decision file
- Update pattern with learnings → update pattern file
- Add entry to changelog → update changelog.md

### File Naming Conventions

**Intent Files:**
- `project-intent.md` - Main project intent
- `feature-*.md` - Feature intents (e.g., `feature-dark-mode.md`)
- `bug-*.md` - Bug fix intents (e.g., `bug-login-timeout.md`)
- `refactor-*.md` - Refactoring intents (e.g., `refactor-auth.md`)

**Decision Files:**
- `001-*.md`, `002-*.md`, ... - Sequential numbering (e.g., `001-jwt-authentication.md`)

**Knowledge Files:**
- `patterns/*.md` - Pattern files (e.g., `jwt-auth-pattern.md`)
- `anti-patterns/*.md` - Anti-pattern files (e.g., `avoid-global-state.md`)

**Evolution Files:**
- `changelog.md` - Main changelog (always updated)
- `learning-*.md` - Learning files (e.g., `learning-api-timeout.md`)

### Linking and Traceability

All files should link to related files for full traceability:

```markdown
## Related
- Intent: feature-dark-mode.md
- Decision: 002-theme-storage.md
- Learning: learning-theme-performance.md
- Pattern: theme-management-pattern.md
```

This creates traceability: Intent → Decision → Learning → Pattern

---

## Avoiding Overdocumentation

**Key Principle**: Use Git for versioning. Create new files only for new scopes.

### When to Create New File

Create a new file when you have a **new scope**:
- ✅ New work item (feature, bug, refactoring) → new intent file
- ✅ New significant decision → new decision file  
- ✅ New pattern/anti-pattern discovered → new knowledge file
- ✅ Important learning that affects future decisions → new learning file

### When to Update Existing File

Update existing file when it's the **same scope** (Git will version it):
- ✅ Refine intent → update intent file
- ✅ Add outcomes to decision → update decision file
- ✅ Evolve pattern with learnings → update pattern file
- ✅ Add changelog entry → update changelog.md
- ✅ Minor corrections, clarifications → update file

### Rule of Thumb

**Ask yourself**: "Is this a new scope or evolution of existing scope?"

- **New scope** → Create new file
- **Same scope** → Update file (Git preserves history)

### Examples

**✅ Good - Update existing:**
- Refining `feature-dark-mode.md` → Update the file (Git shows history)
- Adding outcomes to `001-jwt-authentication.md` → Update the file
- Evolving `jwt-auth-pattern.md` → Update the file

**✅ Good - Create new:**
- New feature "notifications" → Create `feature-notifications.md`
- New bug fix → Create `bug-login-timeout.md`
- New pattern discovered → Create new pattern file

**❌ Avoid - Overdocumentation:**
- Creating `feature-dark-mode-v2.md` when refining → Just update original
- Creating `001-jwt-outcomes.md` → Just add outcomes to original
- Creating pattern version files → Just update original pattern

**Remember**: Git is your version control. Use it. Create files only for new scopes.

---

## Working with Features, Bugs, and Refactoring

Context Mesh applies to **any type of work**:

**New Feature:**
- Step 1: Define feature intent
- Step 2: Build feature with context
- Step 3: Learn and update context

**Bug Fix:**
- Step 1: Define fix intent (what bug, why fix)
- Step 2: Fix bug, document decision
- Step 3: Learn, update context, update changelog

**Refactoring:**
- Step 1: Define refactoring intent
- Step 2: Refactor, document decisions
- Step 3: Learn, preserve patterns

**All follow the same 3-step pattern** - Context Mesh is work-agnostic.

---

## AI-Human Collaboration

### Human Responsibilities
- Lead intent capture and validation
- Supervise AI execution
- Review and approve work
- Validate learnings and insights
- Make critical decisions

### AI Responsibilities
- Generate code based on context
- Suggest solutions and improvements
- Review code for quality
- Help identify what needs updating in context
- Propose context updates

### Collaboration Pattern
- **Intent**: Human leads, AI assists
- **Build**: AI builds, human supervises
- **Learn**: AI analyzes, human validates

---

## Decision Documentation

Every significant decision should be documented with:

- **Context**: What was the situation?
- **Decision**: What did we decide?
- **Rationale**: Why did we decide this?
- **Alternatives**: What else did we consider?
- **Outcomes**: What happened? (updated in Learn step)

**When to Document**:
- Architectural decisions
- Technology choices
- Design patterns
- Important implementation choices

**Format**: Simple markdown or structured format in your context repository.

---

## Framework Principles Alignment

1. **Context as Primary Creation**: Every step creates/updates context
2. **Intent-Driven Architecture**: Architecture flows from intent (Step 1 → Step 2)
3. **Knowledge as Living Entity**: Context evolves continuously (all steps)
4. **Human-AI Collaborative Consciousness**: Clear human-AI roles in each step
5. **Contextual Decision Architecture**: Decisions captured with full context

---

## Integration with Scrum/Agile

Context Mesh can be integrated with Scrum:

- **Sprint Planning**: Use Step 1 (Intent) for each item
- **During Sprint**: Use Step 2 (Build)
- **Sprint Review**: Use Step 3 (Learn)
- **Retrospective**: Refine context and intent

Context Mesh adds:
- Context preservation throughout
- AI agent integration
- Intent-driven development
- Living knowledge evolution
- Decision architecture

---

## Getting Started

1. **Start with Intent**: Define what you want to build and why
2. **Build with Context**: Use AI with full context, supervise and document
3. **Learn and Update**: Update context to reflect code changes, document learnings

See [GETTING_STARTED.md](GETTING_STARTED.md) for detailed implementation guide.
