---
name: build-runner
description: Runs code generation for your framework (e.g., build_runner for Dart, codegen for GraphQL, protobuf compilation, OpenAPI generation). Use after any model, schema, or annotated file change.
---

# Build Runner / Code Generation Skill

Runs code generation tools appropriate to your project's tech stack.

## Common Code Generation Tools

### Dart/Flutter
```bash
dart run build_runner build --delete-conflicting-outputs
```
Generates: Riverpod providers, Freezed models, JSON serialization, Drift DB, Injectable DI

### TypeScript/JavaScript
```bash
# GraphQL codegen
npx graphql-codegen
# OpenAPI client generation
npx openapi-generator-cli generate
# Prisma client
npx prisma generate
```

### Go
```bash
# Protocol Buffers
protoc --go_out=. *.proto
# Wire DI
wire ./...
# sqlc (type-safe SQL)
sqlc generate
```

### Rust
```bash
# Protocol Buffers
cargo build  # build.rs handles protobuf
# sqlx (compile-time SQL checking)
cargo sqlx prepare
```

### Python
```bash
# Pydantic model generation
datamodel-codegen
# Protocol Buffers
protoc --python_out=. *.proto
# SQLAlchemy models
sqlacodegen
```

## Steps

1. Check for any conflicting generated files
2. Run the appropriate code generation command for your stack
3. If generation fails, analyze errors and fix source files
4. Run linter/analyzer to verify no new issues
5. Report what was generated

## When to Run
- After adding/modifying annotated models or schemas
- After changing database table definitions
- After modifying DI/service registrations
- After changing API schemas (GraphQL, OpenAPI, Protobuf)
- After any change to files that feed code generation

## Common Errors
- "Conflicting outputs" — Delete generated files first, then regenerate
- "Generator not found" — Check dev dependencies are installed
- "Missing annotations" — Verify required decorators/annotations are present
