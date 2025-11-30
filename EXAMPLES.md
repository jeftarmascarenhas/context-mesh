# Context Mesh Examples

Real-world examples of Context Mesh in action, showing how the framework is applied in different scenarios.

## Example 1: New Feature Development

### Scenario

A team is building a new user authentication feature for their web application.

### Step 1: Intent

**Intent Statement**:
```markdown
# Intent: User Authentication Feature

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
```

### Step 2: Build

**Implementation**:
- AI generates authentication code based on context (intent)
- Code includes JWT implementation
- Password hashing with bcrypt
- Human reviews and approves

**Decision Record**:
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
- Intent: User Authentication Feature
```

**Context Updates**:
- Code linked to intent
- Decision documented
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

## Context Updates
- Updated decision record with performance notes
- Refined intent: Added performance criteria
```

**Feedback to Intent**:
- Intent refined with performance criteria
- Context updated with learnings

---

## Example 2: Bug Fix with Context

### Scenario

A critical bug is discovered in production: users are unable to log in.

### Step 1: Intent

**Intent**:
```markdown
# Intent: Fix Login Bug

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
```

### Step 2: Build

**Investigation**:
- Root cause: JWT token expiration not handled correctly
- Context: Links to previous authentication implementation

**Fix**:
- Fixed token expiration handling
- Added proper error handling
- Context updated with fix details

**Decision Record**:
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
- Intent: Fix Login Bug
- Previous Decision: JWT-based Authentication
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

## Context Updates
- Updated authentication decision record
- Added test requirements to context
- Improved monitoring setup
```

---

## Example 3: Architecture Refactoring

### Scenario

Team needs to refactor the architecture to support microservices.

### Step 1: Intent

**Intent**:
```markdown
# Intent: Microservices Architecture

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
```

### Step 2: Build

**Implementation**:
- Extract authentication service first
- Implement API Gateway
- Set up service discovery
- Update context with new architecture

**Decision Record**:
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
- Intent: Microservices Architecture
```

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

## Context Updates
- Updated decision record with performance notes
- Refined intent: Added latency tolerance criteria
```

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

## Best Practices from Examples

1. **Always Link to Intent**: Every work item links to original intent
2. **Document Decisions**: All decisions captured with context
3. **Update Context Continuously**: Context updated as work progresses
4. **Learn and Improve**: Learnings feed back to Intent
5. **Validate Against Intent**: Regular validation ensures alignment
6. **Keep Context Simple**: Don't overcomplicate context structure
7. **Use Feedback Loops**: Always feed learnings back to Intent

---

## Common Patterns

### Pattern 1: New Feature
1. **Intent**: Define feature intent
2. **Build**: Implement feature with AI, document decisions
3. **Learn**: Deploy and learn from usage

### Pattern 2: Bug Fix
1. **Intent**: Understand bug and fix intent
2. **Build**: Fix bug, document decision
3. **Learn**: Deploy and verify fix

### Pattern 3: Refactoring
1. **Intent**: Define refactoring intent
2. **Build**: Refactor code, document decisions
3. **Learn**: Deploy and monitor

---

## Further Reading

- [FRAMEWORK.md](FRAMEWORK.md) - Framework details
- [GETTING_STARTED.md](GETTING_STARTED.md) - Getting started
- [INTEGRATION.md](INTEGRATION.md) - Integration guides
