# LCF Frequently Asked Questions

Common questions about the Living Context Framework (LCF).

## General Questions

### What is LCF?

LCF (Living Context Framework) is an AI-First development framework that implements the 5 Philosophical Principles of AI-First Development. It treats context as the primary artifact and code as its manifestation.

### Is LCF a replacement for Scrum/Agile?

No. LCF is **not a replacement** for Scrum, Agile, or other methodologies. It's a complementary framework that adds context preservation and AI-First practices to existing workflows.

### How is LCF different from other frameworks?

LCF is specifically designed for AI-First development, where:
- Context is the primary artifact (not code)
- Intent drives architecture
- Knowledge evolves continuously
- Human-AI collaboration is seamless
- Decisions preserve their "why"

### Do I need special tools to use LCF?

No. LCF is tool-agnostic. You can start with simple file-based context (Markdown + Git) and add tools as needed. See [TOOLS.md](TOOLS.md) for recommendations.

### How simple is LCF compared to Scrum?

LCF is designed to be as simple as Scrum. It has only **3 steps** (compared to Scrum's 5 events), making it easy to learn and adopt. The framework focuses on simplicity while maintaining the power of context preservation.

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

### How does LCF compare to the previous 6-step version?

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

## AI-Human Collaboration Questions

### Do I need AI tools to use LCF?

Not necessarily. LCF defines collaboration patterns, but you can use any AI tools (Cursor, GitHub Copilot, etc.) or even work without AI tools. The framework is about the workflow and context preservation.

### How do AI tools work with humans in LCF?

Clear collaboration patterns:
- **Intent**: Human leads, AI assists
- **Build**: AI generates, human supervises and approves
- **Learn**: AI analyzes, human validates insights

### What AI tools work with LCF?

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

Minor decisions can use simple notes or inline documentation.

### How detailed should Decision Records be?

Decision Records should be:
- Complete enough to understand the decision
- Clear about why the decision was made
- Documented alternatives and implications
- Updated with outcomes (in Learn step)

## Integration Questions

### How do I use LCF with Scrum?

LCF integrates naturally with Scrum:
- **Sprint Planning** → Step 1 (Intent) for each item
- **During Sprint** → Step 2 (Build)
- **Sprint Review** → Step 3 (Learn)
- **Retrospective** → Step 3 (Learn) - refine context and intent

See [INTEGRATION.md](INTEGRATION.md) for details.

### How do I use LCF with Kanban?

LCF works with Kanban:
- **Backlog** → Step 1 (Intent)
- **In Progress** → Step 2 (Build)
- **Done** → Step 3 (Learn)

### How do I use LCF with DevOps?

LCF integrates with DevOps:
- **Plan** → Step 1 (Intent)
- **Code/Build** → Step 2 (Build)
- **Deploy/Operate/Monitor** → Step 3 (Learn)

### Can I use LCF standalone?

Yes! LCF can be used standalone without other frameworks. Just follow the 3 steps:
1. Intent
2. Build
3. Learn

## Adoption Questions

### How do I get started with LCF?

1. Read [FRAMEWORK.md](FRAMEWORK.md) to understand the 3 steps
2. Read [GETTING_STARTED.md](GETTING_STARTED.md) for implementation
3. Start with one project or feature
4. Begin with Step 1 (Intent)
5. Iterate and improve

### How long does it take to adopt LCF?

It depends on your team and project:
- **Quick start**: 1-2 days to understand and start using
- **Full adoption**: 1-2 weeks to fully integrate into workflow
- **Mastery**: Ongoing improvement

### What are common challenges when adopting LCF?

Common challenges:
1. **Too much overhead**: Solution - Keep context simple, focus on essentials
2. **Team resistance**: Solution - Show value, start small, get buy-in
3. **Context getting stale**: Solution - Update continuously, make it part of workflow
4. **Not knowing what to document**: Solution - Focus on intent, decisions, learnings

### Can I adopt LCF gradually?

Yes! You can adopt LCF gradually:
1. Start with Step 1 (Intent) only
2. Add Step 2 (Build) when ready
3. Add Step 3 (Learn) when ready
4. Full adoption

## Best Practices Questions

### What are the best practices for LCF?

1. **Start Small**: Begin with one step or one project
2. **Keep Context Simple**: Don't overcomplicate
3. **Update Continuously**: Keep context current
4. **Link Everything**: Link code, decisions, learnings to intent
5. **Learn Regularly**: Extract learnings frequently
6. **Iterate**: Refine your LCF implementation over time

### How do I know if I'm using LCF correctly?

You're using LCF correctly if:
- Context is always up-to-date
- Intent guides your decisions
- Decisions are documented
- Learnings feed back to intent
- Context is searchable and useful

### What if my team doesn't want to use LCF?

- Show the value of context preservation
- Start with small wins
- Get team input on LCF usage
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
