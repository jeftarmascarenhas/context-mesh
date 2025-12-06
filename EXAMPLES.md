# Context Mesh Examples

Real-world examples of Context Mesh in action, showing how the framework is applied in different scenarios.

## 🎯 Complete End-to-End Example

**New to Context Mesh?** Start here with a complete example:

- **[Todo App Complete Example](examples/todo-app-complete/)** - A full end-to-end demonstration showing:
  - Complete project structure with Context Mesh
  - Intent phase (project intent, features, bugs, decisions)
  - Build phase (implementation with decisions)
  - Learn phase (context updates, learnings, changelog)
  - All artifacts: intents, decisions, patterns, learnings

This example demonstrates the **complete workflow** from planning to learning, with all Context Mesh artifacts in action.

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

## Success Criteria
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

## Success Criteria
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

## Success Criteria
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

## Success Criteria
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
