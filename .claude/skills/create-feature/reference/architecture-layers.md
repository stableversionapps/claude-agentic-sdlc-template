# Clean Architecture Layers

## Layer Overview

```
Presentation Layer (UI)
  |
  v
Domain Layer (Business Logic)
  ^
  |
Data Layer (Repositories, APIs, DB)
```

## Layer Rules

### Presentation Layer
- Contains: UI components, screens, state management
- Imports: Domain layer interfaces ONLY
- Never: Import data layer directly, import external SDKs
- Responsibilities: Render UI, handle user input, manage UI state

### Domain Layer
- Contains: Entities, repository interfaces, use cases, business rules
- Imports: Nothing external (pure language constructs only)
- Never: Import framework code, external packages, or data layer
- Responsibilities: Define business rules, validate data, orchestrate use cases

### Data Layer
- Contains: Repository implementations, data sources, DTOs, API clients
- Imports: Domain interfaces (to implement them), external packages
- Responsibilities: Data access, API calls, caching, mapping DTOs to entities

## Dependency Flow

```
Presentation -> Domain <- Data
```

Presentation depends on Domain.
Data depends on Domain.
Domain depends on NOTHING.

## Repository Pattern

```
// Domain layer — abstract interface
interface UserRepository {
  getById(id: string): Promise<User>
  save(user: User): Promise<void>
  watchAll(): Stream<User[]>
}

// Data layer — implementation
class UserRepositoryImpl implements UserRepository {
  constructor(
    private localDataSource: UserLocalDataSource,
    private remoteDataSource?: UserRemoteDataSource,
    private syncQueue?: SyncQueue
  )

  async save(user: User): Promise<void> {
    // 1. Write to local (always, instant)
    await this.localDataSource.insert(user)

    // 2. Enqueue for sync (if remote available)
    if (this.remoteDataSource) {
      await this.syncQueue.enqueue('users', user.id, 'upsert')
    }
  }
}
```

## Use Case Pattern

```
// Single responsibility — one use case per business operation
class CreateUserUseCase {
  constructor(private repo: UserRepository, private validator: UserValidator)

  async execute(input: CreateUserInput): Result<User> {
    // 1. Validate
    const validation = this.validator.validate(input)
    if (!validation.isValid) return Result.failure(validation.errors)

    // 2. Create entity
    const user = User.create(input)

    // 3. Persist
    await this.repo.save(user)

    // 4. Return
    return Result.success(user)
  }
}
```
