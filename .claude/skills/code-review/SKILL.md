---
name: code-review
description: Reviews code changes and pull requests for quality, architecture compliance, security, and project conventions. Enforces all 7 quality gates. Use before committing, merging, or for PR reviews.
argument-hint: "optional: PR number"
---

# Code Review & PR Review

Reviews code for project standards and enforces all quality gates.

## Usage
`/code-review` — Review current changes vs main
`/code-review <pr-number>` — Review a specific GitHub PR

## Review Pipeline

### Step 1: Static Analysis
Run project linter and formatter with strict settings.

### Step 2: Architecture Compliance
- Feature-first structure with clean architecture layers
- No cross-feature imports (features communicate via shared interfaces)
- No data layer imports in presentation layer
- State management follows project conventions
- All DB access via data access layer
- Domain models use proper serialization
- Repository pattern with abstract interfaces

### Step 3: Code Quality
- No unused imports or dead code
- Proper null safety
- Error handling (no swallowed exceptions)
- No hardcoded strings (use constants or i18n)
- No hardcoded colors/sizes (use theme system and design tokens)
- Proper resource cleanup/disposal
- Immutable constructors used wherever possible

### Step 4: Domain-Specific Rules
- Business rule integrity maintained
- Data handling follows conventions
- Domain edge cases covered

### Step 5: Security
- No hardcoded secrets
- No sensitive data in logs
- Input validation
- Data encryption verified

### Step 6: Tests
- 80%+ coverage on changed code
- All tests pass
- Edge cases covered

### Step 7: Performance
- No unnecessary re-renders/rebuilds
- Virtualized lists for large datasets
- Indexed queries
- No blocking main thread operations

## Verdict
- **APPROVE** — All gates pass
- **REQUEST CHANGES** — Critical/high issues found
- **NEEDS DISCUSSION** — Architectural decisions to align on

## Output Format
```
## [filename]
### Issues (must fix)
- [LINE:XX] Description — suggested fix

### Warnings (should fix)
- [LINE:XX] Description — concern

### Suggestions (nice to have)
- [LINE:XX] Improvement

### Strengths
- What was done well
```

Report issues by severity: CRITICAL -> HIGH -> MEDIUM -> LOW
