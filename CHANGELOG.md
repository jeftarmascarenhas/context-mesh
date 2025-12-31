# Changelog

All notable changes to Context Mesh will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2025-01-XX

### Added
- Optional initial patterns creation in `new-project.md` prompt
  - Users can now add patterns during project initialization
  - Template for pattern files included
  - Maintains flexibility (patterns can be added later via `learn-update.md`)
- Explicit bidirectional linking instructions in all prompts
  - Feature files must link to their decision files
  - Decision files must link back to their feature files
  - Standardized markdown link format: `- [Type: Name](path/to/file.md)`
- Reference to complete AGENTS.md template
  - All prompts that create AGENTS.md now reference `examples/AGENTS.md.example`
  - Users can see complete template with advanced features

### Changed
- Improved prompt templates for better consistency
  - All prompts now use standardized link format
  - Templates updated to match examples in repository
- Enhanced `new-project.md` with hybrid approach
  - Features creation is now optional (can be added later)
  - Patterns creation is now optional (can be added later)
  - Maintains simplicity while allowing complete setup
- Updated `add-feature.md` with explicit bidirectional linking
  - Instructions for creating proper links between features and decisions
  - Template shows correct link format
- Updated `update-feature.md` to maintain links when updating
  - Instructions to update Related sections when links change
  - Ensures bidirectional links remain correct after updates
- Improved `existing-project.md` and `freelance-project.md` templates
  - Corrected link formats to match framework standards
  - Added bidirectional linking instructions

### Fixed
- Fixed missing bidirectional links between features and decisions
  - All prompts now create proper links in both directions
  - Links follow consistent format across all files
- Corrected link format in templates
  - Changed from `- Intent: file.md` to `- [Type: Name](path/to/file.md)`
  - Matches format used in example projects

---

## [1.0.0] - 2024-12-XX

### Added
- Initial release of Context Mesh framework
- Complete 3-step workflow (Intent, Build, Learn)
- Comprehensive documentation:
  - README.md with storytelling and visual diagrams
  - FRAMEWORK.md with detailed workflow explanation
  - GETTING_STARTED.md with quick start guide
  - PRINCIPLES.md explaining the 5 AI-First principles
  - FAQ.md with common questions
  - GLOSSARY.md with key terms
  - COMPARISON.md comparing with other frameworks
  - INTEGRATION.md for Scrum/Agile integration
  - ADVANCED.md for advanced patterns
  - TOOLS.md with tooling recommendations
  - EXAMPLES.md with real-world use cases
- Example projects:
  - Weather App Minimal (simple example)
  - Todo App Complete (full-featured example)
- Prompt templates for common scenarios:
  - new-project.md
  - existing-project.md
  - freelance-project.md
  - add-feature.md
  - fix-bug.md
  - update-feature.md
  - learn-update.md
  - create-agent.md
- Mermaid diagrams for visual workflow representation
- AGENTS.md integration support
- MIT License

### Features
- Context as primary artifact philosophy
- Intent-driven architecture
- Living knowledge repository
- Human-AI collaboration patterns
- Decision documentation with full context
- Pattern and anti-pattern tracking
- Integration with Scrum, Kanban, and DevOps
- Customizable workflow
- Tool-agnostic design

---

[1.1.0]: https://github.com/jeftarmascarenhas/context-mesh/releases/tag/v1.1.0
[1.0.0]: https://github.com/jeftarmascarenhas/context-mesh/releases/tag/v1.0.0

