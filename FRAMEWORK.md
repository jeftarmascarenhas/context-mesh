# Living Context Framework (LCF) - Framework Structure

## Framework Overview

The Living Context Framework (LCF) is an AI-First development framework that implements the 5 Philosophical Principles of AI-First Development. LCF treats context as the primary creation, with code as its manifestation, enabling sustainable AI-assisted development.

**LCF is not a replacement for Scrum or Agile** - it's a complementary framework specifically designed for AI-First development that can be used alongside existing methodologies.

## The 3-Step LCF Workflow

LCF is designed for simplicity and easy adoption, similar to Scrum. The framework consists of three essential steps that preserve context throughout the development lifecycle:

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
- Documents basic hypotheses

**Activities**:
- Define intent (what and why)
- Create initial context
- Document basic hypotheses
- Align stakeholders

**Context Artifacts**:
- Intent Statement (what and why)
- Initial Context
- Basic Hypotheses

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
- Documented Hypotheses

**Definition of Done**:
- [ ] Intent statement is clear and validated
- [ ] Initial context created
- [ ] Basic hypotheses documented
- [ ] Stakeholders aligned

**Principles Applied**:
- ✅ **Context as Primary Creation** - Context is created first
- ✅ **Intent-Driven Architecture** - Intent guides everything

---

### Step 2: Build

**Purpose**: AI builds with context, human supervises, and decisions are documented.

**What it does**:
- AI generates code using living context
- Human supervises and validates
- Decisions are documented in context
- Context is continuously updated

**Activities**:
- AI generates code using living context
- Human supervises and validates AI work
- Document implementation decisions
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

**Definition of Done**:
- [ ] Code implemented using context
- [ ] Important decisions documented
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

**Purpose**: Learn from results and update living context.

**What it does**:
- Observes results (metrics, feedback, behavior)
- Extracts learnings
- Updates living context
- Refines intent if needed
- Creates feedback loop to Intent

**Activities**:
- Observe system behavior (metrics, logs, user feedback)
- Extract learnings and insights
- Update living context with learnings
- Refine intent based on outcomes
- Create new hypotheses
- Feed insights back to Intent step

**Context Artifacts**:
- Learning Insights Document
- Updated Context
- Refined Intent (if needed)
- New Hypotheses
- Outcome Analysis

**Human Role**:
- Validate insights and learnings
- Make improvement decisions
- Refine intent based on outcomes
- Approve context updates

**AI Role**:
- Analyze metrics and extract learnings
- Identify patterns and insights
- Suggest context updates
- Propose intent refinements

**Outputs**:
- Learning Insights
- Updated Living Context
- Refined Intent (if needed)
- New Hypotheses
- Feedback to Intent

**Definition of Done**:
- [ ] Results observed and analyzed
- [ ] Learnings extracted and validated
- [ ] Living context updated with learnings
- [ ] Intent refined if needed
- [ ] Feedback loop to Intent initiated

**Principles Applied**:
- ✅ **Knowledge as Living Entity** - Knowledge evolves
- ✅ **Context as Primary Creation** - Context is updated
- ✅ **Intent-Driven Architecture** - Intent is refined

---

## Feedback Loop

### Primary Feedback Loop: Learn → Intent

**Mechanism**: Insights from Step 3 (Learn) feed directly back to Step 1 (Intent)

**Flow**:
1. Learnings from results → New hypotheses
2. Outcome analysis → Intent refinement
3. Context evolution → Enhanced intent
4. Updated decisions → Better future decisions

**Context Updates**:
- Living context automatically evolves
- Intent statements refined
- Hypotheses updated
- New work items created from learnings

---

## Living Context

Living Context is the central knowledge repository that:

- **Stores**: Intent, hypotheses, decisions, implementation details, learnings
- **Evolves**: Continuously updates as system changes
- **Traces**: Full traceability from intent to code to outcomes
- **Connects**: Links intent → decisions → code → learnings

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
- Analyze metrics and extract insights
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

LCF can be integrated with Scrum:

- **Sprint Planning**: Use Step 1 (Intent) for each item
- **During Sprint**: Use Step 2 (Build)
- **Sprint Review**: Use Step 3 (Learn)
- **Retrospective**: Refine context and intent

LCF adds:
- Context preservation throughout
- AI agent integration
- Intent-driven development
- Living knowledge evolution
- Decision architecture

---

## Getting Started

1. **Start with Intent**: Define what you want to build and why
2. **Build with Context**: Use AI with full context, supervise and document
3. **Learn and Update**: Observe results, learn, update context, refine intent

See [GETTING_STARTED.md](GETTING_STARTED.md) for detailed implementation guide.
