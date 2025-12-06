# Context Mesh Glossary

Key terms and concepts used in Context Mesh.

## A

### ADR (Architecture Decision Record)
A document that captures an architectural decision with its context, rationale, alternatives considered, and implications. ADRs are living documents updated with outcomes. **Decisions can be created in any step** (Intent, Build, or Learn), but the framework recommends planning them in Step 1 (Intent) for faster Build phase.

### AI Agent
An AI-powered assistant that performs specific tasks within the Context Mesh workflow. Context Mesh defines five agent types: Planner, Developer, Reviewer, DevOps, and Insights. Agents can be structured as files (`agents/agent-*.md`) for advanced patterns. See [ADVANCED.md](ADVANCED.md) for details.

### AGENTS.md
An open format used by over 20,000 open-source projects to guide AI coding agents. AGENTS.md works seamlessly with Context Mesh as a **router** that references Context Mesh files for strategic context while providing operational instructions (setup, commands, conventions). See [TOOLS.md](TOOLS.md) for integration details.

### AI-First Development
A development philosophy where AI tools are integrated throughout the development lifecycle, and context is treated as the primary artifact.

## C

### Changelog
A document that records significant changes to the codebase. Updated in Step 3 (Learn) to document what changed and why.

### Context
The knowledge, information, and understanding that surrounds and informs development work. In Context Mesh, context is the primary artifact.

### Context Artifact
A document, record, or piece of information that preserves context. Examples include intent statements, ADRs, and learning documents.

### Context Graph
A knowledge graph that shows relationships between context artifacts, creating a network of connected knowledge.

### Context Hub
See Living Context Hub.

### Context Preservation
The practice of maintaining and updating context throughout the development lifecycle, ensuring knowledge is not lost.

### Context Traceability
The ability to trace relationships between context artifacts, from intent to code to outcomes.

### Context Versioning
The practice of versioning context artifacts, similar to code versioning, to track context evolution over time.

## D

### Definition of Done
A checklist of criteria that must be met before a step or work item is considered complete. Each Context Mesh step has its own Definition of Done.

### DevOps Agent
An AI agent responsible for managing deployment, configuring observability, and ensuring deployment traceability.

### Developer Agent
An AI agent responsible for generating code based on context, suggesting technical solutions, and implementing features.

## F

### Feedback Loop
A mechanism that feeds learnings and insights from later steps back to earlier steps, creating continuous improvement.

## G

### Governance
The framework of rules, processes, and standards that guide how Context Mesh is implemented and how context is managed.

## I

### Intent
The purpose, goal, or objective of a project or feature. Intent is captured in Step 1 (Intent) and guides all subsequent work.

### Intent-Driven Architecture
An architectural approach where architecture is designed to fulfill intent, rather than just technical requirements.

## K

### Knowledge
The accumulated patterns, anti-patterns, and learnings that evolve with the system. Stored in `context/knowledge/` and used throughout all steps.

### Knowledge Graph
A graph structure that represents knowledge as nodes (entities) and edges (relationships), showing how context artifacts are connected.

## L

### Learn
Step 3 of Context Mesh, where context is updated to reflect code changes, learnings are documented, and insights feed back to Intent.

### Living Context
Context that evolves and updates continuously, staying current with the system it describes.

### Context Mesh
The AI-First development framework that implements the 5 Philosophical Principles of AI-First Development. Context Mesh consists of 3 steps: Intent, Build, and Learn.

## M

### Micro-ADR
A smaller ADR that documents implementation-level decisions, as opposed to architectural decisions.

## P

### Pattern
A documented solution that works well, with context about when to use it, why it works, and examples. Patterns are stored in `context/knowledge/patterns/` and used during Build.

### Anti-pattern
A documented solution to avoid, with context about why it's problematic and what problems it causes. Anti-patterns are stored in `context/knowledge/anti-patterns/` and used during Build to avoid known issues.

### Principle
A fundamental truth or belief that guides the framework. Context Mesh is based on 5 AI-First principles.

## S

### Security by Design
A security approach where security is built into the framework from the ground up, not added as an afterthought.

## T

### Traceability
The ability to trace relationships and dependencies between artifacts, from intent to code to outcomes.

## W

### Work Agreement
A team agreement that defines how the team will work together within the Context Mesh framework, including context update frequency, decision documentation standards, and AI agent usage protocols.

## Related Concepts

### Agile
A software development methodology focused on iterative development, collaboration, and responding to change. Context Mesh can be used alongside Agile.

### DevOps
A set of practices that combines software development and IT operations. Context Mesh integrates with DevOps practices.

### Scrum
An Agile framework with defined roles, events, and artifacts. Context Mesh complements Scrum by adding context preservation.

### Waterfall
A sequential software development methodology. Context Mesh represents a shift away from waterfall's linear approach.

## Further Reading

- [FRAMEWORK.md](FRAMEWORK.md) - Framework structure
- [PRINCIPLES.md](PRINCIPLES.md) - The 5 AI-First principles
- [FAQ.md](FAQ.md) - Frequently asked questions

