# AGENTS.md

## Setup Commands
- Install: `npm install`
- Dev: `npm run dev`
- Test: `npm test`
- Build: `npm run build`

## Code Style
- TypeScript strict mode
- Tailwind CSS for styling
- Follow patterns from `@context/knowledge/patterns/`

## Context Files to Load

Before starting work, load:
- @context/intent/project-intent.md (always)
- @context/intent/feature-*.md (for specific feature)
- @context/decisions/*.md (relevant decisions)
- @context/knowledge/patterns/*.md (patterns to follow)

## Project Structure
root/
├── AGENTS.md
├── context/
│   ├── intent/
│   ├── decisions/
│   ├── knowledge/
│   ├── agents/
│   └── evolution/
└── [code]

## AI Agent Rules

### Always
- Load context before implementing
- Follow decisions from @context/decisions/
- Use patterns from @context/knowledge/patterns/
- Update context after implementation

### Never
- Ignore documented decisions
- Use anti-patterns from @context/knowledge/anti-patterns/
- Leave context stale

### After Implementation (Critical)
AI must update Context Mesh after changes:
- Mark feature/bug as completed in intent file
- Add outcomes to decision files
- Update changelog.md
- Create learning-*.md if significant insights

## Definition of Done (Build Phase)

Before completing implementation:
- [ ] ADR exists before implementation
- [ ] Code follows Context Mesh patterns
- [ ] Decisions respected
- [ ] Tests passing
- [ ] Context updated
- [ ] Changelog updated
- [ ] Acceptance Criteria met

