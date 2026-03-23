---
paths:
  - "test/**/*"
  - "tests/**/*"
  - "spec/**/*"
  - "__tests__/**/*"
  - "integration_test/**/*"
  - "e2e/**/*"
---

# Test Conventions

<!-- Customize paths above for your project structure -->

## General
- Use the project's preferred mocking library
- Descriptive test names: `'should [behavior] when [condition]'`
- Group related tests with describe/group blocks
- Test behavior, not implementation details
- Test file structure mirrors source structure
- Use setUp/tearDown for fixtures

## Coverage
- Target 80%+ coverage on domain and data layers
- UI tests: all screens render in both themes
- Integration: all critical user flows
- **Critical paths require 100% coverage:** core business logic, auth flows, data integrity rules

## Test Types
- **Unit:** Domain entities, use cases, validators, utilities
- **UI/Widget:** Screen rendering, interactions, state changes, both themes
- **Integration:** End-to-end user flows, data persistence, navigation
- **Snapshot/Golden:** Design system components, key screens, both themes

## Best Practices
- Mock external dependencies, test domain logic directly
- Test edge cases: empty, null, boundary values, error conditions
- Verify both themes in UI tests
- Keep tests fast — mock slow dependencies
