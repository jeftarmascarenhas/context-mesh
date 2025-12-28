# Context Mesh Frequently Asked Questions

> ❓ **Reference** - Look here when you have questions. You don't need to read it all upfront.
> Start with [README.md](README.md) and [GETTING_STARTED.md](GETTING_STARTED.md).

---

Common questions about Context Mesh.

## General Questions

### What is Context Mesh?

Context Mesh is an AI-First development framework that implements the 5 Philosophical Principles of AI-First Development. It treats context as the primary artifact and code as its manifestation.

### Is Context Mesh a replacement for Scrum/Agile?

No. Context Mesh is **not a replacement** for Scrum, Agile, or other methodologies. It's a complementary framework that adds context preservation and AI-First practices to existing workflows.

### How is Context Mesh different from other frameworks?

Context Mesh is specifically designed for AI-First development, where:
- Context is the primary artifact (not code)
- Intent drives architecture
- Knowledge evolves continuously
- Human-AI collaboration is seamless
- Decisions preserve their "why"

### Do I need special tools to use Context Mesh?

No. Context Mesh is tool-agnostic. You can start with simple file-based context (Markdown + Git) and add tools as needed. See [TOOLS.md](TOOLS.md) for recommendations.

### How simple is Context Mesh compared to Scrum?

Context Mesh is designed to be as simple as Scrum. It has only **3 steps** (compared to Scrum's 5 events), making it easy to learn and adopt. The framework focuses on simplicity while maintaining the power of context preservation.

## Framework Questions

### Why 3 steps? Why not more or fewer?

The 3-step structure balances simplicity with completeness:
- **Intent**: Define what and why (foundation)
- **Build**: Create with context (execution)
- **Learn**: Improve from results (evolution)

This structure is:
- Simple enough to understand quickly
- Complete enough to cover the full lifecycle
- Flexible enough to adapt to different needs

### What are the 3 steps?

1. **Intent** - Define intent and create living context
2. **Build** - AI builds with context, human supervises, decisions documented
3. **Learn** - Learn from results, update context, refine intent

See [FRAMEWORK.md](FRAMEWORK.md) for complete details.

### Can I skip steps?

It depends. Some steps can be minimal (e.g., Intent for bug fixes), but all steps should be considered. The framework is flexible - adapt it to your needs while preserving context.

### How long does each step take?

It varies by project and step:
- **Step 1 (Intent)**: Minutes to hours (for small items) or days (for large features)
- **Step 2 (Build)**: Days to weeks (depending on scope)
- **Step 3 (Learn)**: Ongoing (continuous learning)

### How does Context Mesh compare to the previous 6-step version?

The 3-step version is a simplification that:
- Removes complexity while keeping essential concepts
- Combines related activities (e.g., Review is part of Build)
- Focuses on the core workflow
- Makes adoption easier

The 3 steps cover the same ground as the previous 6 steps, just more simply.

## Context Questions

### What is "Living Context"?

Living Context is context that evolves and updates continuously, staying current with the system it describes. It's not static documentation - it's a living knowledge repository.

### How do I create and maintain Living Context?

Start simple:
1. Create a `context/` directory
2. Add subdirectories: `intent/`, `decisions/`, `learnings/`
3. Use Markdown files for context artifacts
4. Version control with Git

See [GETTING_STARTED.md](GETTING_STARTED.md) for details.

### How often should I update context?

It depends on your workflow. Common approaches:
- **Per task**: Update when task is completed
- **Daily**: Update at end of day
- **Per sprint**: Update at sprint boundaries

Start with per task or daily, adjust based on team needs. The key is to keep context current.

### What if context gets out of sync with code?

This is a common concern. Solutions:
- Update context as you work (during Build step)
- Regular context reviews (during Learn step)
- Link context to code (don't duplicate it)
- Use Git for versioning
- Make context updates part of your workflow

### How do I keep context simple?

- Focus on what matters (intent, decisions, learnings)
- Don't overcomplicate structure
- Use simple markdown files
- Link everything to intent
- Update continuously

### When should I use project-intent.md vs feature-*.md vs bug-*.md?

**Use `project-intent.md` for:**
- Overall project vision and purpose
- High-level project goals and objectives
- General project scope (not individual features)
- Project-wide principles and guidelines

**Update `project-intent.md` only when:**
- Project scope changes significantly (adding/removing major areas)
- High-level goals or objectives change
- Project principles or strategic direction changes

**Use `feature-*.md` for:**
- Each new feature (create `feature-*.md` file)
- Updating existing features (update the existing `feature-*.md` file)
- Do NOT update `project-intent.md` for individual features

**Use `bug-*.md` for:**
- Each bug fix (create `bug-*.md` file)
- Do NOT update `project-intent.md` for bugs

**Rule of thumb**: `project-intent.md` = overall scope. Features/bugs = individual files.

### What should I do when a feature is removed or replaced?

**Deprecate, don't delete**. When a feature is removed or replaced:

1. Update the `feature-*.md` file
2. Add "Status: Deprecated" section with date and reason
3. Link to replacement feature if applicable
4. Keep the file for history and traceability

**Example:**
```markdown
## Status: Deprecated (2024-01-15)
This feature was replaced by feature-new-approach.md.

## Reason
[Why it was deprecated]
```

Git preserves all history, so deprecated files remain accessible and provide valuable context.

### When should I update a feature file vs create a new one?

**General Rule**: Update the same file when it's the same feature evolving. Only create a new file when it's a completely different feature.

**Update `feature-*.md` (same file)** when:
- Adding functionality to existing feature (e.g., adding OAuth to auth feature)
- Refining requirements or acceptance criteria
- Changing technical approach (create new decision file, update feature file)
- Expanding scope of same feature

**Create new `feature-*.md`** when:
- It's a completely different feature (not an evolution)
- Replacing feature entirely (then deprecate old one)
- Splitting one feature into multiple features

**Example - Update same file:**
```
feature-user-auth.md:
- Original: Email/password auth
- Update 1: Add password reset
- Update 2: Add OAuth (Google, GitHub)
- Update 3: Add MFA
→ All updates to same file, Git preserves history
```

**Example - Create new file:**
```
feature-user-auth.md (deprecated)
feature-auth-v2.md (new, complete replacement)
→ Different architecture, completely new approach
```

**How to document significant changes in same file:**
Add a "Change History" section to track major updates:
```markdown
## Change History

### 2024-03-15 - OAuth Integration
- What: Added OAuth providers
- Why: User request
- Impact: New decision 005-oauth.md created
```

**Remember**: Git is your version control. Use it. Update same file for same feature evolution. Create new file only for truly different features.

### When I update a feature and execute the agent, will AI only make the necessary changes?

**Yes, if you guide it correctly.** When updating an existing feature, the AI should:

1. **Analyze existing code first** - Understand what's already implemented
2. **Identify what needs to change** - Compare updated intent with current code
3. **Make incremental changes only** - Modify only what's necessary
4. **Preserve existing code** - Don't regenerate code that doesn't need to change

**How to ensure AI makes only necessary changes:**

When executing after updating a feature, use this prompt:

```
Update the existing feature following @context/intent/feature-[name].md.

IMPORTANT: This is an UPDATE to existing code, not a new implementation.
- First, analyze the existing code for this feature
- Identify what needs to change based on the updated intent
- Make ONLY the necessary modifications
- Preserve existing code that doesn't need to change
- Follow the "Changes from Original" section if present in the intent file
```

**Best practices:**
- Always mention "UPDATE" or "MODIFY" in your prompt, not "IMPLEMENT" or "CREATE"
- Reference the existing code explicitly: "Update the existing [feature name] feature"
- If the intent file has a "Changes from Original" section, the AI will follow it
- Review the AI's plan before it executes (Plan, Approve, Execute pattern)

**Example:**
```
❌ Bad: "Implement user authentication following @context/intent/feature-user-auth.md"
→ AI might regenerate everything

✅ Good: "Update the existing user authentication feature following @context/intent/feature-user-auth.md. Make only the necessary changes to add OAuth support."
→ AI will analyze existing code and add only OAuth
```

### What should I do when a bug is fixed?

**Mark as resolved, don't delete**. When a bug is fixed:

1. Update the `bug-*.md` file
2. Add "Status: Resolved" section with date and resolution details
3. Link to related commits or changelog
4. Keep the file for history and traceability

**Example:**
```markdown
## Status: Resolved (2024-01-15)
Bug fixed in commit abc123. See: changelog.md

## Resolution
[How it was fixed]
```

## AI-Human Collaboration Questions

### Do I need AI tools to use Context Mesh?

Not necessarily. Context Mesh defines collaboration patterns, but you can use any AI tools (Cursor, GitHub Copilot, etc.) or even work without AI tools. The framework is about the workflow and context preservation.

### How do AI tools work with humans in Context Mesh?

Clear collaboration patterns:
- **Intent**: Human leads, AI assists
- **Build**: AI generates, human supervises and approves
- **Learn**: AI analyzes, human validates insights

### What AI tools work with Context Mesh?

Any AI development tools work:
- Cursor
- GitHub Copilot
- Codeium
- Tabnine
- Or any other AI coding assistant

The framework is tool-agnostic.

## Decision Documentation Questions

### What is a Decision Record?

A Decision Record documents a decision with:
- **Context**: What was the situation?
- **Decision**: What did we decide?
- **Rationale**: Why did we decide this?
- **Alternatives**: What else did we consider?
- **Outcomes**: What happened? (updated in Learn step)

### When do I need a Decision Record?

Create Decision Records for:
- Major architectural decisions
- Technology choices
- Design patterns
- Significant implementation decisions
- Asset management decisions (where to store images, JSON files, how to organize, external integrations)

Minor decisions can use simple notes or inline documentation.

### When should I create Decision Records?

**Decisions can be created in any step**, but the framework recommends planning them in Step 1 (Intent) for faster Build phase:

- **Step 1 (Intent) - Recommended**: Plan technical decisions when you know the approach. This makes Build faster since AI has decisions ready.
- **Step 2 (Build)**: Create decisions if technical choices emerge during implementation (common for bug fixes or when discovering better approaches).
- **Step 3 (Learn)**: Update decisions with outcomes or create improvement decisions based on learnings.

The framework is flexible - create decisions when it makes sense for your workflow.

### How detailed should Decision Records be?

Decision Records should be:
- Complete enough to understand the decision
- Clear about why the decision was made
- Documented alternatives and implications
- Updated with outcomes (in Learn step)

### How do I document asset management decisions?

Assets (images, JSON files, static files, design assets from Figma, etc.) should be documented in decisions when you make technical choices about them:

**Document in `decisions/` when:**
- Choosing where to store assets (local, CDN, S3, etc.)
- Deciding asset organization structure
- Choosing formats (PNG vs SVG, JSON schemas)
- Setting up external integrations (Figma MCP, design tools)
- Making optimization decisions

**Document in `knowledge/patterns/` when:**
- Establishing patterns for asset organization
- Creating naming conventions
- Defining asset workflow (design → code)

**Mention in `feature-*.md` when:**
- Assets are part of a specific feature
- Feature requires specific assets (images, icons, data files)

**Example Decision:**
```markdown
# Decision: Asset Management Strategy

## Context
We need to manage images, icons, and design assets for the frontend.

## Decision
- Store images locally in `public/images/`
- Use Figma MCP for design handoff
- Optimize images before commit
- Use SVG for icons, PNG for photos

## Rationale
- Local storage: faster development, no external dependencies
- Figma MCP: direct design-to-code workflow
- Optimization: better performance
```

## Integration Questions

### How do I use Context Mesh with Scrum?

Context Mesh integrates naturally with Scrum:
- **Sprint Planning** → Step 1 (Intent) for each item
- **During Sprint** → Step 2 (Build)
- **Sprint Review** → Step 3 (Learn)
- **Retrospective** → Step 3 (Learn) - refine context and intent

See [INTEGRATION.md](INTEGRATION.md) for details.

### How do I use Context Mesh with Kanban?

Context Mesh works with Kanban:
- **Backlog** → Step 1 (Intent)
- **In Progress** → Step 2 (Build)
- **Done** → Step 3 (Learn)

### How do I use Context Mesh with DevOps?

Context Mesh integrates with DevOps:
- **Plan** → Step 1 (Intent)
- **Code/Build** → Step 2 (Build)
- **Deploy/Operate/Monitor** → Step 3 (Learn)

### Can I use Context Mesh standalone?

Yes! Context Mesh can be used standalone without other frameworks. Just follow the 3 steps:
1. Intent
2. Build
3. Learn

## Adoption Questions

### How do I get started with Context Mesh?

1. Read [FRAMEWORK.md](FRAMEWORK.md) to understand the 3 steps
2. Read [GETTING_STARTED.md](GETTING_STARTED.md) for implementation
3. Start with one project or feature
4. Begin with Step 1 (Intent)
5. Iterate and improve

### How long does it take to adopt Context Mesh?

It depends on your team and project:
- **Quick start**: 1-2 days to understand and start using
- **Full adoption**: 1-2 weeks to fully integrate into workflow
- **Mastery**: Ongoing improvement

### What are common challenges when adopting Context Mesh?

Common challenges:
1. **Too much overhead**: Solution - Keep context simple, focus on essentials
2. **Team resistance**: Solution - Show value, start small, get buy-in
3. **Context getting stale**: Solution - Update continuously, make it part of workflow
4. **Not knowing what to document**: Solution - Focus on intent, decisions, learnings

### Can I adopt Context Mesh gradually?

Yes! You can adopt Context Mesh gradually:
1. Start with Step 1 (Intent) only
2. Add Step 2 (Build) when ready
3. Add Step 3 (Learn) when ready
4. Full adoption

## Best Practices Questions

### What are the best practices for Context Mesh?

1. **Start Small**: Begin with one step or one project
2. **Keep Context Simple**: Don't overcomplicate
3. **Update Continuously**: Keep context current
4. **Link Everything**: Link code, decisions, learnings to intent
5. **Learn Regularly**: Extract learnings frequently
6. **Iterate**: Refine your Context Mesh implementation over time

### How do I know if I'm using Context Mesh correctly?

You're using Context Mesh correctly if:
- Context is always up-to-date
- Intent guides your decisions
- Decisions are documented
- Learnings feed back to intent
- Context is searchable and useful

### What if my team doesn't want to use Context Mesh?

- Show the value of context preservation
- Start with small wins
- Get team input on Context Mesh usage
- Make it optional initially
- Demonstrate benefits

## Technical Questions

### What file format should I use for context?

Markdown is recommended because:
- Simple and readable
- Version control friendly
- Easy to edit
- Works with any tools

But you can use any format that works for your team.

### How do I version control context?

Use Git (or similar):
- Commit context updates regularly
- Track context evolution
- Link context to code commits
- Use branches for context changes

### Can I automate context updates?

Yes, you can automate:
- Context updates from code changes
- Context validation
- Context linking
- Context search

But start simple and add automation as needed.

## Further Reading

- [FRAMEWORK.md](FRAMEWORK.md) - Framework details
- [GETTING_STARTED.md](GETTING_STARTED.md) - Getting started guide
- [INTEGRATION.md](INTEGRATION.md) - Integration guides
- [EXAMPLES.md](EXAMPLES.md) - Real-world examples
- [PRINCIPLES.md](PRINCIPLES.md) - The 5 AI-First principles
