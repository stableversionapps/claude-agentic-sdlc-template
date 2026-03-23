---
name: performance-check
description: Profiles and optimizes application performance — rendering, memory, database queries, startup time. Ensures performance targets are met.
---

# Performance Check

Profiles and optimizes the application for target performance metrics.

## Usage
`/performance-check` — Full performance audit
`/performance-check <area>` — Audit specific area (rendering/memory/db/startup/network)

## Targets

<!-- Customize for your platform -->

| Metric | Target | Critical |
|--------|--------|----------|
| Cold Start | < 3s | < 5s |
| Page Transition | < 300ms | < 500ms |
| DB Query | < 100ms | < 250ms |
| Frame Rate | 60fps+ | > 45fps |
| Memory (idle) | < 150MB | < 200MB |
| Bundle Size | < [TARGET] | < [CRITICAL] |

## Checks

### Rendering
- Immutable constructors used where possible
- No logic in view/build methods
- Repaint boundaries on heavy subtrees
- Virtualized/lazy lists for all scrollable content

### State Management
- Narrow state scoping with selectors
- Auto-dispose on transient state
- No synchronous heavy work in state handlers

### Database
- Indices on queried columns
- Paginated queries for large tables
- Batch operations in transactions
- Precomputed aggregates for dashboards

### Memory
- Resources (controllers/subscriptions) disposed
- Image cache limits set
- No full-table loads into memory

### Startup
- Lazy service initialization
- Deferred heavy queries after first render
- Splash/loading screen covers initialization

### Network
- Request batching
- Response caching with TTL
- Compression enabled
- Connection pooling
