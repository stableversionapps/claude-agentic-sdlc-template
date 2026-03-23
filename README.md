# Claude Code Agentic Template

A production-ready template for building software with [Claude Code](https://docs.anthropic.com/en/docs/claude-code) using a multi-agent, skill-based agentic framework. Clone this repo and customize it for any project — Flutter, React, Python, Go, Rust, or any other stack.

## What This Is

This template provides a complete agentic development framework for Claude Code with:

- **15 specialized AI agents** that work in parallel for maximum development velocity
- **21 reusable skills** covering the full software development lifecycle
- **4 path-scoped rules** that auto-activate based on which files you're editing
- **SDLC workflow** with parallel analysis, implementation, and quality gates
- **Zero-noise design philosophy** baked into every UI-related agent and skill
- **Story-based tracking** with file-based sprint boards and backlogs

## Architecture

```
your-project/
+-- CLAUDE.md                    # Project identity, conventions, agent/skill docs
+-- .mcp.json                    # MCP server configuration
+-- .gitignore                   # Standard gitignore
+-- .claude/
|   +-- settings.json            # Permissions, hooks, safety guards
|   +-- output-styles/
|   |   +-- minimal.md           # Terse output style
|   +-- agents/                  # 15 specialist agents
|   |   +-- scrum-master.md      # SDLC orchestrator
|   |   +-- moderator.md         # Quality gate enforcer
|   |   +-- architect.md         # Principal engineer
|   |   +-- ui-designer.md       # UI/UX architect
|   |   +-- ai-engineer.md       # AI/ML engineer
|   |   +-- code-reviewer.md     # Code quality
|   |   +-- security-analyst.md  # Security engineering
|   |   +-- market-researcher.md # Competitive intelligence
|   |   +-- database-architect.md# Database specialist
|   |   +-- test-engineer.md     # Testing strategy
|   |   +-- performance-engineer.md # Performance optimization
|   |   +-- devops-engineer.md   # CI/CD & deployment
|   |   +-- api-integrator.md    # API integration
|   |   +-- accessibility-expert.md # WCAG compliance
|   |   +-- user-researcher.md   # UX research
|   +-- skills/                  # 21 specialized skills
|   |   +-- sdlc-orchestration/  # EPIC decomposition & sprint management
|   |   +-- create-feature/      # Clean architecture scaffolding
|   |   +-- design-screen/       # Screen/page design with zero-noise
|   |   +-- design-system/       # Design token enforcement
|   |   +-- create-widget/       # Reusable component creation
|   |   +-- code-review/         # Code & PR review
|   |   +-- testing/             # Test strategy & generation
|   |   +-- deployment/          # CI/CD & release
|   |   +-- api-integration/     # External API patterns
|   |   +-- performance/         # Performance optimization
|   |   +-- accessibility/       # WCAG audit
|   |   +-- security-audit/      # Security assessment
|   |   +-- documentation/       # ADRs & changelogs
|   |   +-- market-research/     # Competitive analysis
|   |   +-- user-research/       # UX research & archetypes
|   |   +-- ai-features/         # AI feature patterns
|   |   +-- offline-first/       # Offline-first architecture
|   |   +-- cloud-agnostic/      # Provider-agnostic design
|   |   +-- build-runner/        # Code generation
|   |   +-- analytics-chart/     # Data visualization
|   |   +-- ocr-receipt/         # Document scanning & OCR
|   +-- rules/                   # Path-scoped auto-rules
|       +-- code-conventions.md  # Code style & patterns
|       +-- ui-rules.md          # Zero-noise UI rules
|       +-- data-rules.md        # Data layer rules
|       +-- test-rules.md        # Test conventions
+-- .stories/                    # Sprint tracking
    +-- SPRINT-BOARD.md          # Current sprint view
    +-- BACKLOG.md               # Prioritized EPIC list
```

## Agents

| Agent | Model | Role |
|-------|-------|------|
| **scrum-master** | opus | SDLC orchestrator, parallel agent launcher, sprint management |
| **moderator** | opus | Quality gate enforcer, conflict resolution, standards enforcement |
| **architect** | opus | Principal engineer — system design, clean architecture, implementation |
| **ui-designer** | opus | UI/UX architect — zero-noise philosophy, timeless design |
| **ai-engineer** | opus | AI/ML — invisible intelligence, Claude API, privacy-first |
| **code-reviewer** | opus | Code quality — architecture compliance, all 5 component states |
| **security-analyst** | opus | Security — OWASP Top 10, encryption, auth, privacy |
| **market-researcher** | opus | Competitive intelligence — gap analysis, differentiation |
| **database-architect** | sonnet | Database — schema design, migrations, query optimization |
| **test-engineer** | sonnet | Testing — unit, UI, integration, 80%+ coverage |
| **performance-engineer** | sonnet | Performance — profiling, optimization, targets |
| **devops-engineer** | sonnet | DevOps — CI/CD, builds, deployment, environments |
| **api-integrator** | sonnet | APIs — external service integration, resilience patterns |
| **accessibility-expert** | sonnet | Accessibility — WCAG 2.1 AA, cognitive a11y |
| **user-researcher** | sonnet | UX — archetypes, cognitive load, usability validation |

## SDLC Workflow

The framework drives development through 4 parallel phases per feature:

```
Phase 1: PARALLEL ANALYSIS
  6 agents analyze simultaneously: user research, architecture,
  UI design, security, market research, database design

Phase 2: PARALLEL IMPLEMENTATION
  Independent tracks run simultaneously: database, domain logic,
  UI components, AI features

Phase 3: PARALLEL QUALITY GATES
  6 agents review simultaneously: code review, testing, security,
  accessibility, performance, design compliance

Phase 4: ACCEPTANCE
  Verify all criteria met, zero regressions, update story status
```

## Getting Started

### 1. Clone the template

```bash
git clone https://github.com/[YOUR_USERNAME]/claude-agentic-template.git my-project
cd my-project
rm -rf .git && git init
```

### 2. Customize CLAUDE.md

Open `CLAUDE.md` and replace all `[BRACKETED_PLACEHOLDERS]`:

- `[YOUR_PROJECT_NAME]` — Your project name
- `[YOUR_PLATFORM]` — Flutter, React, Python, Go, etc.
- `[YOUR_STATE_MANAGEMENT]` — Riverpod, Redux, Zustand, etc.
- `[YOUR_DATABASE]` — PostgreSQL, SQLite, MongoDB, etc.
- `[YOUR_SOURCE_DIR]` — `lib`, `src`, `app`, etc.
- All design tokens (colors, fonts, spacing)
- Business rules specific to your domain
- Build phases and performance targets

### 3. Customize rules

Update the `paths` in each rule file (`.claude/rules/*.md`) to match your project's file structure.

### 4. Customize settings.json

Update `.claude/settings.json`:

- **PostToolUse hooks**: Replace the generic reminder with your framework's formatter/linter command
- **Stop hooks**: Replace with your project's analyzer command
- **env**: Add any environment variables your project needs

Example for a Flutter project:
```json
{
  "PostToolUse": [{
    "matcher": "Edit|Write",
    "hooks": [{
      "type": "command",
      "command": "FILE=$(echo \"$TOOL_INPUT\" | grep -oE '[^ ]*\\.dart' | head -1); if [ -n \"$FILE\" ] && [ -f \"$FILE\" ]; then dart format \"$FILE\" 2>/dev/null; fi"
    }]
  }],
  "Stop": [{
    "hooks": [{
      "type": "command",
      "command": "dart analyze --no-fatal-infos 2>&1 | tail -5"
    }]
  }]
}
```

### 5. Add MCP servers (optional)

Edit `.mcp.json` to add project-specific MCP servers:

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    },
    "supabase": {
      "type": "url",
      "url": "https://mcp.supabase.com/mcp"
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"]
    }
  }
}
```

### 6. Set up story tracking

Edit `.stories/BACKLOG.md` with your project's EPICs and features.

### 7. Start building

```bash
claude
# Then use agents:
# "Use the scrum-master to plan EPIC-01"
# "Use the architect to build the auth feature"
# "Use the code-reviewer to review my changes"
```

## Customization Guide

### Adding a new agent

Create `.claude/agents/my-agent.md`:

```markdown
---
name: my-agent
description: What this agent does. Use when [trigger].
tools: Read, Edit, Write, Bash, Grep, Glob, Agent, WebSearch, WebFetch
model: opus  # or sonnet
effort: max  # or high
memory: project
isolation: worktree  # for code-writing agents
skills:
  - relevant-skill
maxTurns: 30
---

# Agent Name

You are a **[role]** specializing in [domain].

## Your Responsibilities
...

## When Invoked
...
```

### Adding a new skill

Create `.claude/skills/my-skill/SKILL.md`:

```markdown
---
name: my-skill
description: What this skill does. Use when [trigger].
argument-hint: "optional usage hint"
---

# Skill Name

Description and usage instructions.

## Steps
1. ...
2. ...
```

### Adding a new rule

Create `.claude/rules/my-rule.md`:

```markdown
---
paths:
  - "src/**/my-pattern/**/*"
---

# Rule Name

- Rule 1
- Rule 2
```

## Design Philosophy

This template embeds a **zero-noise design philosophy** into every UI-related agent and skill:

- Every screen answers only 1 primary question
- Maximum 3 primary actions per view
- Spacing over borders (no decorative elements)
- All 5 component states: default, loading, empty, error, success
- Skeleton shimmer for loading (never spinners)
- Both light and dark themes from day one
- Motion = meaning (no decorative animation)
- WCAG 2.1 AA accessibility compliance

## Quality Gates

Every feature must pass ALL 7 gates before merge:

1. **Architecture** — Clean architecture compliance
2. **Code Review** — Quality, conventions, zero-noise UI
3. **Security** — OWASP compliance, no secrets, encryption
4. **Testing** — 80%+ coverage, all tests passing
5. **UI Design** — Design system match, all 5 states, both themes
6. **Accessibility** — WCAG 2.1 AA, screen reader, contrast
7. **Performance** — Meets target metrics

## Priority Order

When agents disagree or trade-offs arise:

**Security > Correctness > UX > Performance > Features**

## License

MIT License. Use this template for any project.

---

Built for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) by the community.
