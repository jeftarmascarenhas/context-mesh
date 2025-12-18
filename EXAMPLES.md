# Context Mesh Examples

> 📚 **Deep Dive** - This is optional reading. You can start using Context Mesh without reading this.
> Start with [README.md](README.md) and [GETTING_STARTED.md](GETTING_STARTED.md).
> For hands-on examples, see [examples/](examples/).

---

Real-world examples of Context Mesh in action, showing how the framework is applied in different scenarios.

---

## 💼 Business Value

### For Development Teams

- **Reduced time** wasted on context reconstruction ([McKinsey Research](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/yes-you-can-measure-software-developer-productivity) shows developers spend significant time on context recovery)
- **Faster** developer onboarding
- **Dramatically improved** code quality and maintainability
- **Faster** delivery cycles
- **Reduced time** for heavy documentation tasks

### For Organizations

- **Faster time-to-market**: Build in days/weeks instead of months
- **Lower onboarding costs**: New developers productive in days, not weeks
- **Better code quality**: Code remains comprehensible for years
- **Reduced technical debt**: Decisions preserved with full context
- **AI-ready**: Maximize ROI on AI development tools

### ROI Example

**Theoretical Calculation:**
A team of 10 developers saving time on context reconstruction (based on research showing developers spend significant time on context recovery) can result in substantial cost savings. The exact ROI depends on your team size, hourly rates, and specific context challenges.

---

## 🌟 Success Stories

Context Mesh is being used in production by teams building and modernizing real-world applications.

### Real-World Success Story

**AI Automation Platform Front-End Migration** 🏢
- **2 developers** migrated the **front-end** of a complex React monolith into **10 micro front-ends** in **15 days**
- The monolith was an **automation platform for software development workflows using AI**, containing **10 internal tools**
- **Legacy codebase**: medium-to-high complexity per tool, hard to understand, **no consistent standards**
- **Result**: Migration completed in 15 days by planning each tool with Context Mesh, then building with AI using that context

**How Context Mesh Made It Possible:**
- Ran **Intent (plan)** for each tool before coding (about **4–5 days** total)
- Used **Build + Learn** for the remaining time, updating context whenever needed
- Each micro front-end got its own preserved context (intent, decisions, patterns, evolution)
- AI could implement changes safely because the technical approach and standards were documented up front

**What changed in the Build step:**
- Migrated each tool to a **newer React** baseline
- Switched UI from **Material UI → shadcn/ui**
- Introduced **React Query** (previously not used)
- Adopted `@module-federation/vite` for micro front-end composition

**Key Achievement**: What typically takes months of planning and migration was completed in **15 days** with just 2 developers, thanks to Context Mesh's structured approach to context preservation.

**Another real example:**
- Built [`context-mesh.org`](https://context-mesh.org) with **2–3 hours** in Intent planning and **< 1 hour** in Build, then Learn to keep context current

### Common Benefits Teams Experience

- ✅ **Faster delivery cycles** - Context preservation reduces time spent on understanding and reconstruction
- ✅ **Reduced documentation overhead** - Context Mesh structure makes documentation part of the workflow
- ✅ **Faster development cycles** - AI tools work more effectively with rich context
- ✅ **Faster onboarding** - New developers productive in days instead of weeks
- ✅ **Better code quality** - Decisions and patterns preserved with full context

### Use Cases in Production

✅ **Monolith to Micro Front-ends**: Large-scale application decomposition  
✅ **Legacy Modernization**: COBOL, JavaScript, Python code transformation  
✅ **Team Scaling**: Faster onboarding and knowledge transfer  
✅ **Complex Tool Migration**: Multi-tool platforms with preserved context  
✅ **Design-to-Code**: Seamless integration with design workflows (Figma)

### Join The Community

*We're working with teams to share detailed case studies and company logos. Coming soon!*

**Using Context Mesh?** [Share your success story →](https://github.com/jeftarmascarenhas/context-mesh/discussions)

**Want to be featured?** We'd love to showcase how Context Mesh is helping your team achieve faster, better development.

---

## 🎯 Complete End-to-End Examples

**New to Context Mesh?** Start with one of these examples:

### Weather App Minimal (Recommended for Beginners)

**[examples/weather-app-minimal/](examples/weather-app-minimal/)** - 45-60 minutes

- Simple setup, no database
- Modern stack: Vite + React + Fastify
- 3 phases with dedicated agents

**Quick Start:**
```bash
cd examples/weather-app-minimal
cat EXECUTION_GUIDE.md  # Follow step-by-step
```

### Todo App Complete (Full Workflow)

**[examples/todo-app-complete/](examples/todo-app-complete/)** - 2-3 hours

- Full-stack with authentication
- PostgreSQL + Prisma
- Testing and CI/CD
- 7 phases with dedicated agents

**Quick Start:**
```bash
cd examples/todo-app-complete
cat EXECUTION_GUIDE.md  # Follow step-by-step
```

Both examples include:
- **EXECUTION_GUIDE.md** - Step-by-step execution with DoD for each phase
- **Agents** - Execute each phase with `@context/agents/agent-*.md`
- **Complete context** - Intent, decisions, patterns, evolution

---

## Example 1: New Feature Development

### Scenario

A team is building a new user authentication feature for their web application.

### Step 1: Intent

**Feature Intent** (created as `feature-authentication.md`):
```markdown
# Intent: Feature - User Authentication

## What
Build a secure user authentication system that allows users to sign up,
log in, and manage their accounts.

## Why
- Users need secure access to the application
- Current system lacks proper authentication
- Security is a critical requirement

## Acceptance Criteria
- Users can sign up with email and password
- Users can log in securely
- Passwords are hashed and stored securely
- Session management works correctly
- Security best practices followed

## Related
- Project Intent: project-intent.md
- Decision: 001-jwt-authentication.md
```

**Technical Decision** (created in Step 1 - recommended approach):
```markdown
# Decision: JWT-based Authentication

## Context
We need to implement user authentication. We considered JWT tokens vs.
session-based authentication.

## Decision
Use JWT tokens for authentication.

## Rationale
- Stateless authentication scales better
- Works well with microservices architecture
- Industry standard approach
- Supports mobile apps easily

## Alternatives Considered
- Session-based: More complex, requires session storage
- OAuth: Overkill for our use case

## Related
- Intent: feature-authentication.md
```

**Note**: Decisions can be created in any step, but planning them in Step 1 makes the Build phase faster since AI has the technical approach ready.

### Step 2: Build

**Implementation**:
- AI generates authentication code based on context (intent + decisions from Step 1)
- Code includes JWT implementation (following decision from Step 1)
- Password hashing with bcrypt
- Human reviews and approves

**Note**: If a new technical choice emerges during Build, you can create a new decision file. The framework is flexible - you can create decisions in Step 1, Step 2, or Step 3 as needed.

**Context Updates**:
- Code linked to intent (`feature-authentication.md`)
- Code linked to decision (`001-jwt-authentication.md`)
- Implementation details added to context

### Step 3: Learn

**Deployment**:
- Deployed to production
- Observability configured
- Metrics collected

**Learnings**:
```markdown
# Learning: Authentication Performance

## Insight
JWT token validation is fast, but we noticed some latency in
password hashing during sign-up.

## Impact
Sign-up takes 200ms longer than expected.

## Action
- Optimize bcrypt rounds if needed
- Consider async password hashing
- Monitor performance
```

**Context Updates**:
- Updated decision record (`001-jwt-authentication.md`) with outcomes:
  ```markdown
  ## Outcomes
  - JWT implementation successful
  - Token validation fast (< 5ms)
  - Password hashing adds 200ms latency (acceptable)
  ```
- Updated feature intent (`feature-authentication.md`) with performance criteria
- Context updated with learnings

**Feedback to Intent**:
- Feature intent refined with performance criteria
- Decision record updated with outcomes
- Context updated with learnings

---

## Example 2: Bug Fix with Context

### Scenario

A critical bug is discovered in production: users are unable to log in.

### Step 1: Intent

**Bug Intent** (created as `bug-login-failure.md`):
```markdown
# Intent: Fix Bug - Login Failure

## What
Fix the bug preventing users from logging in.

## Why
- Critical production issue
- Users cannot access the application
- Business impact is high

## Acceptance Criteria
- Users can log in successfully
- Bug root cause identified and fixed
- Prevention measures in place

## Related
- Feature: feature-authentication.md
- Decision: (will be created if needed during Build)
```

**Note**: For bug fixes, decisions are often created during Step 2 (Build) after investigating the root cause. However, if you already know the fix approach, you can create the decision in Step 1.

### Step 2: Build

**Investigation**:
- Root cause: JWT token expiration not handled correctly
- Context: Links to previous authentication implementation (`feature-authentication.md`)

**Fix**:
- Fixed token expiration handling
- Added proper error handling
- Context updated with fix details

**Decision Record** (created during Build - common for bug fixes):
```markdown
# Decision: Token Expiration Handling Fix

## Context
Users unable to log in due to missing token expiration check.

## Decision
Add comprehensive token expiration handling in authentication middleware.

## Rationale
- Prevents login failures
- Improves user experience
- Aligns with security best practices

## Related
- Intent: bug-login-failure.md
- Previous Decision: 001-jwt-authentication.md
```

### Step 3: Learn

**Deployment**:
- Hotfix deployed
- Monitoring increased
- Users can log in again

**Learnings**:
```markdown
# Learning: Token Expiration Handling

## Insight
We didn't properly handle JWT token expiration, causing login failures.

## Root Cause
Token expiration check was missing in authentication middleware.

## Prevention
- Added comprehensive tests for token expiration
- Updated decision record with expiration handling requirements
- Added monitoring for authentication failures
```

**Context Updates**:
- Updated bug intent (`bug-login-failure.md`) - marked as resolved:
  ```markdown
  ## Status: Resolved (2024-01-15)
  Bug fixed in commit abc123. See: changelog.md
  
  ## Resolution
  Added comprehensive token expiration handling in authentication middleware.
  ```
- Updated decision record (`001-jwt-authentication.md`) with expiration handling requirements
- Updated fix decision with outcomes
- Added test requirements to context
- Improved monitoring setup

---

## Example 3: Architecture Refactoring

### Scenario

Team needs to refactor the architecture to support microservices.

### Step 1: Intent

**Refactoring Intent** (created as `refactor-microservices.md`):
```markdown
# Intent: Refactor - Microservices Architecture

## What
Refactor monolithic application into microservices architecture.

## Why
- Need better scalability
- Teams need independence
- Technology diversity required

## Acceptance Criteria
- Services are independently deployable
- Services communicate via APIs
- No breaking changes for users
- Performance maintained or improved

## Related
- Project Intent: project-intent.md
- Decision: 002-microservices-architecture.md
```

**Technical Decision** (created in Step 1 - recommended for architectural decisions):
```markdown
# Decision: Microservices Architecture with API Gateway

## Context
Current monolithic architecture limits scalability and team independence.
Need to move to microservices.

## Decision
Adopt microservices architecture with API Gateway pattern.

## Rationale
- Better scalability
- Team independence
- Technology flexibility
- Industry best practice

## Alternatives Considered
- Monolith with modules: Doesn't solve scalability
- Serverless: Too early, need more control

## Related
- Intent: refactor-microservices.md
```

### Step 2: Build

**Implementation**:
- Extract authentication service first
- Implement API Gateway (following decision from Step 1)
- Set up service discovery
- Update context with new architecture

### Step 3: Learn

**Deployment**:
- Services deployed gradually
- Monitoring enhanced
- Performance tracked

**Learnings**:
```markdown
# Learning: Microservices Performance

## Insight
API Gateway adds 50ms latency, but overall system is more scalable.

## Impact
- Slight latency increase acceptable
- Better scalability achieved
- Team independence improved

## Actions
- Optimize API Gateway
- Consider caching
- Monitor performance
```

**Context Updates**:
- Updated decision record (`002-microservices-architecture.md`) with outcomes:
  ```markdown
  ## Outcomes
  - Microservices architecture successfully implemented
  - API Gateway adds 50ms latency (acceptable trade-off)
  - Better scalability achieved
  - Team independence improved
  ```
- Updated refactoring intent (`refactor-microservices.md`) with latency tolerance criteria
- Context updated with learnings

---

## Example 4: Context Mesh + Scrum Integration

### Scenario

A Scrum team adopts Context Mesh for their sprints.

### Sprint Planning (Step 1: Intent)

**Activities**:
- Review backlog items
- For each item, define intent (what and why)
- Plan context preservation tasks
- Connect sprint to context

**Output**:
- Sprint backlog with intent for each item
- Context tasks included
- Sprint goal linked to intent

### During Sprint (Step 2: Build)

**Activities**:
- Build with context
- Document decisions
- Update context continuously
- Daily context updates

**Example**:
- "Yesterday: Implemented feature X, updated context with decisions"
- "Today: Will continue feature X, need to document decision"
- "Blockers: Need context on API design"

### Sprint Review (Step 3: Learn)

**Activities**:
- Demo with intent validation
- Review context preservation
- Validate against original intent
- Extract learnings

**Output**:
- Review report with context
- Feedback linked to context
- Intent validation results

### Sprint Retrospective (Step 3: Learn)

**Activities**:
- Extract learnings
- Update context
- Feed insights to Intent
- Improve context practices

**Output**:
- Learnings document
- Updated context
- Improvement actions
- New hypotheses

---

## Example 5: Deprecating a Feature

### Scenario

A team decides to replace an old feature with a new approach.

### Step 1: Intent

**New Feature Intent** (created as `feature-new-approach.md`):
```markdown
# Intent: Feature - New Approach

## What
Replace old feature with new, improved approach.

## Why
- Old approach has limitations
- New approach provides better UX
- Technical improvements available

## Acceptance Criteria
- New feature implemented
- Old feature deprecated
- Migration path for existing users
```

### Step 2: Build

**Implementation**:
- New feature implemented
- Migration path created
- Old feature marked as deprecated

### Step 3: Learn

**Deprecation** (update existing `feature-old-approach.md`):
```markdown
# Intent: Feature - Old Approach

## What
[Original feature description]

## Why
[Original reasons]

## Status: Deprecated (2024-01-15)
This feature was replaced by feature-new-approach.md.

## Reason
- Limitations in old approach
- Better UX with new approach
- Technical improvements available

## Migration
See: feature-new-approach.md for migration guide.
```

**Note**: Do NOT delete deprecated features. Keep them for history and traceability. Git preserves all history.

---

## Best Practices from Examples

1. **Always Link to Intent**: Every work item links to original intent
2. **Plan Decisions in Step 1**: Create technical decisions in Step 1 when you know the approach (makes Build faster)
3. **Flexibility with Decisions**: Decisions can be created in any step - create in Step 2 or Step 3 if needed
4. **Use Feature Files**: Create `feature-*.md` for features, `bug-*.md` for bugs, `project-intent.md` for overall scope
5. **Deprecate, Don't Delete**: Mark features/bugs as deprecated or resolved, but keep files for history
6. **Update Context Continuously**: Context updated as work progresses
7. **Learn and Improve**: Learnings feed back to Intent
8. **Validate Against Intent**: Regular validation ensures alignment
9. **Keep Context Simple**: Don't overcomplicate context structure
10. **Use Feedback Loops**: Always feed learnings back to Intent

---

## Common Patterns

### Pattern 1: New Feature
1. **Intent**: Create `feature-*.md`, plan decisions (recommended)
2. **Build**: Implement feature with AI, use decisions from Step 1 or create new ones if needed
3. **Learn**: Deploy, update decisions with outcomes, learn from usage

### Pattern 2: Bug Fix
1. **Intent**: Create `bug-*.md`
2. **Build**: Fix bug, create decision if needed (often created during Build after investigation)
3. **Learn**: Mark bug as resolved, update decisions with outcomes, deploy and verify fix

### Pattern 3: Refactoring
1. **Intent**: Create `refactor-*.md`, plan architectural decisions (recommended)
2. **Build**: Refactor code, use decisions from Step 1 or create new ones if needed
3. **Learn**: Deploy, update decisions with outcomes, monitor

---

## Further Reading

- [FRAMEWORK.md](FRAMEWORK.md) - Framework details
- [GETTING_STARTED.md](GETTING_STARTED.md) - Getting started
- [INTEGRATION.md](INTEGRATION.md) - Integration guides
- [TOOLS.md](TOOLS.md) - AGENTS.md integration
- [examples/AGENTS.md.example](../examples/AGENTS.md.example) - Example AGENTS.md with Context Mesh
