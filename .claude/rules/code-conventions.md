---
paths:
  - "src/**/*"
  - "lib/**/*"
  - "app/**/*"
---

# Code Conventions

<!-- Customize paths above and rules below for your tech stack -->

## Architecture
- Feature-first folder structure: `[SOURCE_DIR]/features/<feature>/presentation|domain|data`
- Clean architecture layers: Presentation -> Domain <- Data
- No cross-layer imports that violate dependency rules
- Repository pattern with abstract interfaces in domain layer

## State Management
- Use your framework's idiomatic state management with code generation where available
- All state classes should handle: loading, data, and error states
- No business logic in view/render methods — extract to state management layer

## Data Access
- All database queries via typed data access objects (DAOs/repositories)
- No raw queries in presentation layer
- Use reactive streams for list screens where possible
- Money/currency as integers — NEVER floating point

## Code Quality
- Use theme system — never hardcode colors or text styles
- Immutable constructors wherever possible
- Run code generation after modifying annotated/schema files
- Proper error handling — no swallowed exceptions
- No hardcoded strings — use constants or i18n
