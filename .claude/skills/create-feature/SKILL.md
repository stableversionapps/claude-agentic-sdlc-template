---
name: create-feature
description: Scaffolds a new feature module with clean architecture layers (presentation, domain, data). Use when starting a new feature.
argument-hint: "feature-name"
---

# Create Feature Skill

Scaffolds a complete feature module following clean architecture.

## Steps

1. Read the feature requirements from the project requirements document
2. Create the feature directory structure:
   ```
   [YOUR_SOURCE_DIR]/features/<feature_name>/
   +-- data/
   |   +-- datasources/
   |   |   +-- <feature>_local_datasource.[ext]
   |   |   +-- <feature>_remote_datasource.[ext]  (if needed)
   |   +-- repositories/
   |       +-- <feature>_repository_impl.[ext]
   +-- domain/
   |   +-- entities/
   |   |   +-- <entity>.[ext]
   |   +-- repositories/
   |   |   +-- <feature>_repository.[ext]  (abstract/interface)
   |   +-- usecases/
   |       +-- <usecase>.[ext]
   +-- presentation/
       +-- state/
       |   +-- <feature>_state.[ext]  (state management)
       +-- screens/
       |   +-- <feature>_screen.[ext]
       +-- widgets/
           +-- <widget>.[ext]
   ```
3. Create the domain entity (immutable model)
4. Create the abstract repository interface
5. Create the repository implementation
6. Create the state management layer
7. Create the screen scaffold with proper theming
8. Run code generation (if applicable)
9. Verify with linter/analyzer

## Conventions
- Entity names: PascalCase singular (`Account`, `Transaction`, `Budget`)
- File names: snake_case or kebab-case (per language convention)
- State providers: camelCase with appropriate suffix
- Screens: PascalCase with `Screen`/`Page`/`View` suffix
- All state classes use union types for loading/data/error
