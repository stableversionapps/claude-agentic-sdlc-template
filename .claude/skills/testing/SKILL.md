---
name: testing
description: Generates and runs comprehensive tests — unit tests for logic, UI tests for components, integration tests for flows, snapshot tests for visual regression. Targets 80%+ coverage. Use after implementing features or when tests are failing.
argument-hint: "feature|unit|ui|integration|run"
---

# Testing

Generates and runs comprehensive test suites for project features.

## Usage
`/testing run` — Run full test suite with coverage
`/testing <feature>` — Generate all tests for a feature
`/testing unit <file>` — Unit tests for specific file
`/testing ui <screen>` — UI/widget tests for a screen
`/testing integration <flow>` — Integration test for a user flow

## Test Execution

Run all tests with coverage using your framework's test command:
```bash
# Examples for common frameworks:
# Flutter: flutter test --coverage
# Node.js: npx jest --coverage
# Python: pytest --cov
# Go: go test -cover ./...
# Rust: cargo tarpaulin
```

## Test Structure

```
test/
+-- core/
|   +-- database/          # Data access tests
|   +-- design_system/     # Theme/design tests
|   +-- utils/             # Utility tests
+-- features/
|   +-- <feature>/
|       +-- data/
|       |   +-- repositories/<feature>_repository_impl_test.[ext]
|       +-- domain/
|       |   +-- usecases/<usecase>_test.[ext]
|       +-- presentation/
|           +-- state/<feature>_state_test.[ext]
|           +-- screens/<feature>_screen_test.[ext]
+-- integration/
    +-- <flow>_test.[ext]
```

## Testing Strategy

### Unit Tests (80%+ coverage target)
- Domain entities — Model behavior, equality, serialization
- Use cases — Business logic with mocked repositories
- State management — State transitions using test containers
- Business rules — Domain-specific invariants and calculations
- Validators — Input validation, parsing, formatting
- Utilities — Helpers, formatters, converters

### UI / Component Tests
- Screen rendering — All screens render without errors
- User interactions — Click, tap, input behaviors
- State changes — UI updates when state changes
- Error/loading states — Display properly
- Dark mode — Components render correctly in both themes

### Integration Tests
- Auth flows — Login, signup, session management
- CRUD workflows — Create, read, update, delete with verification
- Complex flows — Multi-step user workflows end-to-end
- Navigation — Deep links, back navigation, guards
- Data persistence — Close and reopen, verify data intact

### Snapshot / Golden Tests
- Design system components — Match design spec
- Key screens — Match expected output
- Both themes — Light and dark mode snapshots

## Conventions
- Use your framework's recommended mocking library
- Group related tests with describe/group blocks
- Descriptive test names: `'should [behavior] when [condition]'`
- Use setUp/tearDown for fixtures
- Test behavior, not implementation details
- Test file structure mirrors source structure

## Coverage Targets
- Unit: 80%+ for domain and data layers
- UI: All screens render in both themes
- Integration: All critical user flows
- **Critical paths (100% coverage):** Core business logic, auth flows, data integrity
