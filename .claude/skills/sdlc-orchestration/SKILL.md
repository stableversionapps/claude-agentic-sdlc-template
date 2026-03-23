---
name: sdlc-orchestration
description: Drives the full SDLC process — decomposes EPICs into features, stories, and tasks. Manages story files at .stories/. Orchestrates parallel agents for analysis, design, implementation, and quality gates.
argument-hint: "EPIC-number|sprint N|status|create|update story-id"
---

# SDLC Orchestration & Story Management

Drives end-to-end software delivery with parallel agent orchestration and file-based story tracking.

## Usage
`/sdlc-orchestration EPIC-01` — Decompose and plan an EPIC
`/sdlc-orchestration sprint 1` — Plan a sprint
`/sdlc-orchestration status` — Current progress report
`/sdlc-orchestration create EPIC-01` — Create stories for an EPIC
`/sdlc-orchestration update STORY-001 status done` — Update story status
`/sdlc-orchestration list EPIC-02` — List all stories for an EPIC

## EPIC Decomposition

### Step 1: Read Requirements
- Parse the project requirements document for the target EPIC
- Extract user stories, data models, acceptance criteria
- Identify dependencies on other EPICs

### Step 2: Break Down
```
EPIC -> Features (deliverable capabilities)
  -> User Stories (user-facing value, 1-3 days each)
    -> Tasks (implementable units, 1-4 hours each)
```

### Step 3: Create Story Files
- Directory: `.stories/EPIC-XX/EPIC-XX-FEAT-XX/`
- Files: `STORY-NNN-descriptive-name.md`
- Each story has: user story, AC, success criteria, tasks, dependencies

### Step 4: Parallel Analysis (MANDATORY before implementation)

Launch ALL analysis agents simultaneously:
```
+-- user-researcher    -> User journey, cognitive load, archetype validation
+-- architect          -> System design, data model, interface contracts
+-- ui-designer        -> Screen design, component inventory
+-- security-analyst   -> Threat model, auth flows, data exposure
+-- market-researcher  -> Competitive context, differentiation
+-- database-architect -> Schema design, migration plan, query optimization
```

### Step 5: Parallel Implementation
```
+-- Track A: database-architect -> Schema + data access + migrations
+-- Track B: architect          -> Domain layer + use cases + repositories
+-- Track C: ui-designer        -> Screen components + states + themes
+-- Track D: ai-engineer        -> AI features (if applicable)
```

### Step 6: Parallel Quality Gates
```
+-- code-reviewer        -> Architecture, UI compliance, 5 states
+-- test-engineer        -> Unit/UI tests, 80%+ coverage
+-- security-analyst     -> Security audit
+-- accessibility-expert -> WCAG 2.1 AA
+-- performance-engineer -> Performance metrics
+-- ui-designer          -> Design system match, both themes
```

## Story File Management

### Directory Structure
```
.stories/
+-- SPRINT-BOARD.md
+-- BACKLOG.md
+-- EPIC-01/
|   +-- EPIC-01-FEAT-01/
|   |   +-- STORY-001-initial-setup.md
|   |   +-- STORY-002-database-layer.md
|   +-- EPIC-01-FEAT-02/
|       +-- STORY-003-auth-system.md
+-- EPIC-02/
    +-- ...
```

### Story Template
```markdown
---
id: STORY-NNN
epic: EPIC-XX
feature: FEAT-XX
title: Short descriptive title
status: backlog | ready | in-progress | review | done | blocked
priority: critical | high | medium | low
assignee: agent-name
sprint: N
estimated_hours: N
created: YYYY-MM-DD
updated: YYYY-MM-DD
depends_on: []
blocks: []
---

# STORY-NNN: Title

## User Story
As a [persona], I want [action] so that [benefit].

## Acceptance Criteria
- [ ] AC-1: Testable criterion

## Tasks
- [ ] TASK-1: Description (est: Xh)
```

### Status Flow
```
backlog -> ready -> in-progress -> review -> done
                        |
                     blocked
```

## Solution Quality Standards
Every feature MUST be: futuristic, scalable, extensible, maintainable, zero-regression.
