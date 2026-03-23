---
name: documentation
description: Generates code documentation — API docs, architecture decision records, and changelog entries. Use when decisions need recording.
---

# Documentation

Generates targeted documentation for the project.

## Usage
`/documentation adr <title>` — Create an Architecture Decision Record
`/documentation changelog <version>` — Generate changelog entry
`/documentation api <feature>` — Document API contracts for a feature

## ADR Format

```markdown
# ADR-NNN: Title

## Status: Proposed | Accepted | Deprecated | Superseded

## Context
What problem are we solving?

## Decision
What did we decide and why?

## Consequences
What are the trade-offs?
```

Store in: `docs/adr/NNN-title.md`

## Changelog Format

```markdown
## [version] - YYYY-MM-DD

### Added
- New features

### Changed
- Changes to existing features

### Fixed
- Bug fixes

### Security
- Security fixes
```

## Rules
- Document WHY, not WHAT (code shows what)
- Only add comments for non-obvious logic
- Keep docs close to code (in-file > separate doc)
- ADRs are immutable — supersede, don't edit
