---
paths:
  - "src/**/data/**/*"
  - "src/**/models/**/*"
  - "src/**/repositories/**/*"
  - "lib/**/data/**/*"
  - "lib/**/domain/**/*"
  - "lib/core/database/**/*"
  - "app/**/data/**/*"
---

# Data Layer Rules

<!-- Customize paths above for your project structure -->

## Data Integrity
- Enforce constraints at both application and database level
- Wrap multi-table operations in transactions
- Validate data at boundaries (input validation)
- Maintain audit trail for critical data mutations (timestamps, source)

## Data Handling
- Store monetary amounts as integers (cents, minor units) — NEVER floating point
- Currency code stored alongside amount (ISO 4217)
- Rounding handled explicitly with documented strategy
- Date/time always stored with timezone information

## Database Access
- All queries via typed data access objects — no raw queries outside DAOs
- Reactive streams (watch/subscribe) for list screens
- Add indices on frequently queried columns
- Paginate large result sets

## Data Layer Architecture
- Repository pattern: abstract interface in domain, implementation in data
- Offline-first: local DB is source of truth
- Cloud sync is optional and additive
- No cloud SDK imports in domain or presentation layers
- Error types are domain-specific (not provider error classes)
