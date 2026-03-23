# [YOUR_PROJECT] — Claude Development Guide

<!--
  CUSTOMIZATION: Replace all [BRACKETED_PLACEHOLDERS] with your project-specific values.
  This template works for any tech stack: Flutter, React, Python, Go, Rust, etc.
-->

## Project Identity
- **Public Name:** [YOUR_PROJECT_NAME]
- **Platform:** [YOUR_PLATFORM] <!-- e.g., Flutter (iOS + Android), React (Web), Python (Backend), Go (Microservices) -->
- **Repo:** [YOUR_REPO_NAME]
- **BRD / Requirements Doc:** `[YOUR_BRD_FILE].md` — the single source of truth for all requirements, architecture, data models, and design tokens
- **Vision:** [YOUR_PROJECT_VISION] <!-- One sentence describing the ambitious goal -->

## Architecture
- **State Management:** [YOUR_STATE_MANAGEMENT] <!-- e.g., Riverpod, Redux, Zustand, Vuex, MobX -->
- **Database:** [YOUR_DATABASE] <!-- e.g., Drift (SQLite), PostgreSQL, MongoDB, DynamoDB -->
- **Navigation / Routing:** [YOUR_ROUTER] <!-- e.g., GoRouter, React Router, Next.js App Router -->
- **DI / IoC:** [YOUR_DI_FRAMEWORK] <!-- e.g., GetIt + Injectable, Inversify, Wire, dig -->
- **Auth:** [YOUR_AUTH_PROVIDER] — behind abstract `AuthService` interface
- **AI:** Claude API — behind abstract `AIService` interface
- **Models / Serialization:** [YOUR_MODEL_FRAMEWORK] <!-- e.g., Freezed, Pydantic, Zod, serde -->
- **Layers:** Clean Architecture — Presentation -> Domain <- Data
- **Offline-First:** [YES/NO] <!-- If yes: Local DB is single source of truth; sync is optional -->
- **Cloud-Agnostic:** Abstract interfaces in domain layer; provider implementations swappable via DI

## Design Philosophy

> "The best UI is not minimal — it is *inevitable*."

### Core Principles
1. **Cognitive Load Minimization** — Every screen/page answers only 1 primary question. Max 3 primary actions per view. Progressive disclosure aggressively.
2. **Zero Noise Interface** — No decorative elements without function. Spacing is the layout tool, not borders. Kill: unnecessary borders, excess colors, competing CTAs.
3. **Temporal UX (Flow > Pages)** — Design transitions, not pages. Every interaction answers: What just happened? What can I do next?
4. **Invisible Intelligence** — Default states are smart. System predicts next action, preferences, frequency patterns. App learns user, not the other way around.
5. **Emotional Safety** — Appropriate to your domain. Calm colors, encouraging copy, milestone celebration. Never condescending.

### Component State System (EVERY Component)
All 5 states required: **Default** | **Loading** (skeleton shimmer, never spinner) | **Empty** (helpful + action) | **Error** (message + retry) | **Success** (subtle feedback)

### Motion System
- Motion = meaning. No decorative animation.
- Fast: 100-150ms | Normal: 200-300ms | Emphasis: 400ms
- Always respect reduced-motion system settings

### Screen/Page Rhythm
Every view: **Entry Focus** (understand in < 1s) -> **Action Zone** (max 3 actions) -> **Exit Clarity** (where to go next)

## Design System
<!-- Customize these tokens for your project -->
- **Font:** [YOUR_FONT_FAMILY] (Regular 400 / Medium 500 / SemiBold 600 / Bold 700)
- **Brand Color:** [YOUR_PRIMARY_COLOR] — used sparingly, not as fill
- **Secondary:** [YOUR_SECONDARY_COLOR]
- **Light Background:** [YOUR_LIGHT_BG] / Surface: [YOUR_LIGHT_SURFACE]
- **Dark Mode:** [YOUR_DARK_SURFACE] / [YOUR_DARK_BG]. No shadows in dark — use surface elevation.
- **Semantic Colors:** Success `[COLOR]` / Error `[COLOR]` / Warning `[COLOR]` — contextual only, never decorative
- **Spacing (8pt grid):** xs 4 | sm 8 | md 16 | lg 24 | xl 32 | xxl 48
- **Card Radius:** [VALUE] | **Button Radius:** [VALUE] | **Modal Radius:** [VALUE]
- **Min Touch Target:** 44dp

## Key Business Rules
<!-- Replace with your domain-specific rules -->
- [BUSINESS_RULE_1] <!-- e.g., All transactions use double-entry bookkeeping -->
- [BUSINESS_RULE_2] <!-- e.g., Money amounts stored as integers — NEVER floating point -->
- [BUSINESS_RULE_3] <!-- e.g., Offline-first: all data local, cloud sync is optional -->
- [BUSINESS_RULE_4] <!-- e.g., Privacy-first: no user data sold, AI data anonymized -->

## Dev Conventions
<!-- Replace with your tech-stack-specific conventions -->
- Feature-first folder structure: `[YOUR_SOURCE_DIR]/features/<feature>/presentation|domain|data`
- [YOUR_CODE_GEN_CONVENTION] <!-- e.g., All providers annotated with @riverpod (code generation) -->
- [YOUR_DB_CONVENTION] <!-- e.g., All DB queries via DAOs — no raw SQL in UI layer -->
- [YOUR_MODEL_CONVENTION] <!-- e.g., Use freezed for all domain entities and state classes -->
- [YOUR_BUILD_COMMAND] <!-- e.g., Run `dart run build_runner build` after any model change -->
- Use theme system — never hardcode colors or text styles
- Both light and dark mode from the start — not an afterthought
- Prefer immutable constructors wherever possible
- Spacing for layout structure — no borders or dividers unless functionally required
- Skeleton shimmer for loading states — never spinners for content areas

## Build Phases
<!-- Customize for your project -->
1. **Phase 1 — Foundation** (Week 1): Project scaffold, design system, auth, navigation shell
2. **Phase 2 — Core Features** (Week 2): [YOUR_CORE_FEATURES]
3. **Phase 3 — Extended Features** (Week 3): [YOUR_EXTENDED_FEATURES]
4. **Phase 4 — Integration** (Week 4): [YOUR_INTEGRATIONS]
5. **Phase 5 — Intelligence & Polish** (Week 5): AI features, performance optimization, release

## Performance Targets
<!-- Customize for your platform -->
- Cold start: < 3s | Page transition: < 300ms | DB query: < 100ms
- Frame rate: 60fps+ (if applicable) | Memory (idle): < 150MB | Bundle size: < [TARGET]

## Agentic Framework

### Agents (`.claude/agents/`) — 15 Specialized Roles

| Agent | Role | Model | When to Use |
|-------|------|-------|-------------|
| `scrum-master` | SDLC orchestrator, parallel agent launcher, EPIC decomposition, sprint management | opus | Start work on any EPIC, sprint planning, progress tracking |
| `moderator` | Parallel orchestrator, quality gates, conflict resolution | opus | Complex multi-agent tasks, cross-agent coordination |
| `architect` | Principal engineer — system design, architecture, end-to-end implementation | opus | New features, refactoring, architecture, complex implementation |
| `ui-designer` | UI/UX architect — zero-noise philosophy, component design | opus | Building screens, visual design, components |
| `ai-engineer` | AI/ML engineer — predictive UI, Claude API, privacy-first AI | opus | AI features, categorization, insights, adaptive UI |
| `code-reviewer` | Code reviewer — architecture and quality compliance | opus | Before merging, PR reviews |
| `security-analyst` | Security engineer — OWASP, encryption, auth, data protection | opus | Auth/encryption changes, pre-release |
| `market-researcher` | Market researcher — competitive analysis framework | opus | Feature prioritization, product decisions |
| `database-architect` | Database specialist — schema design, migrations, query optimization | sonnet | Schema design, data access, migrations |
| `test-engineer` | Test engineer — comprehensive testing strategy | sonnet | After feature work, test coverage |
| `performance-engineer` | Performance engineer — profiling and optimization | sonnet | Optimization, profiling, pre-release |
| `user-researcher` | UX researcher — archetypes, cognitive load, usability | sonnet | Feature validation, UX decisions |
| `devops-engineer` | DevOps — CI/CD, builds, deployment, environments | sonnet | Build issues, deployment, releases |
| `api-integrator` | API integration — external service patterns | sonnet | External service integration |
| `accessibility-expert` | Accessibility — WCAG 2.1 AA compliance | sonnet | UI audit, pre-release |

### Skills (`.claude/skills/`) — Specialized Capabilities

#### SDLC & Project Management
| Skill | Purpose |
|-------|---------|
| `sdlc-orchestration` | EPIC -> Feature -> Story -> Task decomposition, sprint execution |

#### Architecture & Development
| Skill | Purpose |
|-------|---------|
| `create-feature` | Scaffold new feature with clean architecture layers |
| `design-screen` | Build screens/pages with zero-noise philosophy and all 5 states |
| `design-system` | Design system token enforcement |
| `create-widget` | Reusable component creation with proper theming and a11y |
| `build-runner` | Code generation patterns |
| `offline-first` | Offline-first patterns: local DB truth, sync queue, conflict resolution |
| `cloud-agnostic` | Abstract interfaces for auth/sync/storage/AI, swappable providers |

#### Integration & AI
| Skill | Purpose |
|-------|---------|
| `api-integration` | External API implementation patterns |
| `ai-features` | Privacy-first AI feature patterns (Claude API) |
| `ocr-receipt` | Document scanning and OCR pipeline |
| `analytics-chart` | Data visualization with zero-noise design |

#### Quality & Review
| Skill | Purpose |
|-------|---------|
| `code-review` | Code review and PR quality gate review |
| `testing` | Test strategy and generation (80%+ coverage) |
| `security-audit` | Comprehensive security assessment |
| `performance` | Profile and optimize against targets |
| `accessibility` | WCAG 2.1 AA + cognitive accessibility audit |

#### Research & Operations
| Skill | Purpose |
|-------|---------|
| `market-research` | Competitive analysis and market trends |
| `user-research` | User archetypes, UX story arc, cognitive load budget |
| `documentation` | ADRs, changelogs, API documentation |
| `deployment` | Build, release, deployment |

### Quality Gates (enforced by moderator)
Every feature must pass ALL gates before merge:
1. Architecture review (`architect`)
2. Code review + zero-noise compliance (`code-reviewer`)
3. Security check (`security-analyst`)
4. Tests passing with 80%+ coverage (`test-engineer`)
5. UI matches design system + all 5 states (`ui-designer`)
6. Accessibility audit (`accessibility-expert`)
7. Performance profiled against targets (`performance-engineer`)

### Path-Scoped Rules (`.claude/rules/`)
Contextual rules auto-loaded when working on matching files:
- `code-conventions.md` — `[YOUR_SOURCE_DIR]/**/*.[EXT]` — Framework conventions, patterns, best practices
- `ui-rules.md` — `[YOUR_SOURCE_DIR]/**/presentation/**/*.[EXT]` — Zero-noise, 5 states, motion, theming
- `data-rules.md` — `[YOUR_SOURCE_DIR]/**/data/**/*.[EXT]` — DB access patterns, data integrity
- `test-rules.md` — `test/**/*.[EXT]` — Testing conventions, coverage targets, naming

### SDLC Workflow

Driven by the `scrum-master` agent with parallel agent orchestration and local file-based tracking:

```
EPIC (from requirements doc)
  |-- Feature (deliverable capability)
        |-- User Story (user-facing value, 1-3 days)
              |-- Task (implementable unit, 1-4 hours)
```

**Story tracking:** `.stories/EPIC-XX/EPIC-XX-FEAT-XX/STORY-NNN-name.md`
**Sprint board:** `.stories/SPRINT-BOARD.md`

**Parallel execution per story (4 phases):**

1. **Parallel Analysis** — Launch simultaneously:
   - `user-researcher` -> user journey, cognitive load, archetype validation
   - `architect` -> system design, data model, interface contracts
   - `ui-designer` -> screen design, component inventory
   - `security-analyst` -> threat model, auth flows, data exposure
   - `market-researcher` -> competitive context, differentiation
   - `database-architect` -> schema design, migration plan, queries

2. **Parallel Implementation** — Launch independent tracks simultaneously:
   - Track A: `database-architect` -> schema + data access + migrations
   - Track B: `architect` -> domain layer + use cases + repositories
   - Track C: `ui-designer` -> screen components + states + themes
   - Track D: `ai-engineer` -> AI features (if applicable)

3. **Parallel Quality Gates** — Launch ALL checks simultaneously:
   - `code-reviewer` + `test-engineer` + `security-analyst` + `accessibility-expert` + `performance-engineer` + `ui-designer`

4. **Accept** — Verify AC met, zero regressions, update story status to `done`

**Status flow:** `backlog -> ready -> in-progress -> review -> done` (or `blocked`)

### Solution Quality Standards
Every solution must be:
- **Futuristic** — design for where the platform is going, not where it is
- **Scalable** — handles 10x growth without architectural changes
- **Extensible** — new capabilities plug in without modifying existing code
- **Maintainable** — any engineer can understand and modify it in 6 months
- **Zero-regression** — never breaks what already works

### Priority Order for Conflicts
**Security > Correctness > UX > Performance > Features**

## Reference
- Full requirements: `[YOUR_BRD_FILE].md`
- Design system reference: `.claude/skills/design-system/reference/component-patterns.md`
- Code review checklist: `.claude/skills/code-review/reference/review-checklist.md`
