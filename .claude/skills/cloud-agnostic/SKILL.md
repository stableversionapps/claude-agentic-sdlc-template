---
name: cloud-agnostic
description: Implements cloud-agnostic, loosely-coupled architecture. Abstract interfaces for auth, sync, storage, and AI — swappable providers without touching business logic. Use when integrating any external service.
user-invocable: false
---

# Cloud-Agnostic Architecture

This project uses a loosely-coupled, provider-agnostic approach. No business logic depends on a specific cloud provider. Every external service is behind an abstract interface.

## Core Principle

> Business logic NEVER imports a cloud SDK directly. It imports an abstract interface. The data layer provides the implementation.

## Abstraction Layers

### 1. Authentication

```
// Domain layer — provider-agnostic interface
interface AuthService {
  watchAuthState(): Stream<AuthState>
  signInWithEmail(email, password): Promise<AuthResult>
  signInWithOAuth(provider): Promise<AuthResult>
  signOut(): Promise<void>
  getCurrentUser(): Promise<AuthUser?>
}

// Data layer — swappable implementations
class SupabaseAuthService implements AuthService { ... }
class FirebaseAuthService implements AuthService { ... }
class Auth0Service implements AuthService { ... }
class LocalAuthService implements AuthService { ... }  // offline dev
```

### 2. Cloud Sync

```
interface SyncService {
  pushChanges(operations): Promise<SyncResult>
  pullChanges(since): Promise<SyncChange[]>
  watchStatus(): Stream<SyncStatus>
  connect(): Promise<void>
  disconnect(): Promise<void>
}

class SupabaseSyncService implements SyncService { ... }
class FirebaseSyncService implements SyncService { ... }
class RestApiSyncService implements SyncService { ... }
class NoOpSyncService implements SyncService { ... }  // offline-only
```

### 3. Remote Storage

```
interface StorageService {
  upload(path, data): Promise<string>
  download(path): Promise<bytes>
  delete(path): Promise<void>
}

class SupabaseStorageService implements StorageService { ... }
class S3StorageService implements StorageService { ... }
class LocalStorageService implements StorageService { ... }
```

### 4. AI Service

```
interface AIService {
  chat(messages): Promise<string>
  classify(input): Promise<Classification>
  generateInsights(summary): Promise<Insight[]>
  parseDocument(text): Promise<StructuredData>
}

class ClaudeAIService implements AIService { ... }
class OpenAIService implements AIService { ... }
class RuleBasedAIService implements AIService { ... }  // offline fallback
```

## Dependency Injection Pattern

```
// Register based on configuration — swap at startup
function configureServices(config) {
  if (config.cloudProvider == 'supabase') {
    container.register(AuthService, SupabaseAuthService)
    container.register(SyncService, SupabaseSyncService)
  } else if (config.cloudProvider == 'firebase') {
    container.register(AuthService, FirebaseAuthService)
    container.register(SyncService, FirebaseSyncService)
  } else {
    container.register(AuthService, LocalAuthService)
    container.register(SyncService, NoOpSyncService)
  }

  if (config.aiEnabled) {
    container.register(AIService, ClaudeAIService)
  } else {
    container.register(AIService, RuleBasedAIService)
  }
}
```

## Layer Rules (ENFORCED)

```
Presentation Layer
  +-- Imports: Domain interfaces ONLY
  +-- Never: import any cloud SDK directly

Domain Layer
  +-- Imports: Pure language constructs only
  +-- Defines: Abstract interfaces (AuthService, SyncService, etc.)
  +-- Never: Any external package import

Data Layer
  +-- Imports: External packages (cloud SDKs, etc.)
  +-- Implements: Domain interfaces
  +-- Contains: Provider-specific code, mapping, error translation
```

## Cloud-Agnostic Checklist (EVERY external integration)

- [ ] Abstract interface defined in domain layer
- [ ] Implementation in data layer
- [ ] No cloud SDK imports outside data layer
- [ ] Offline fallback implementation exists
- [ ] Provider swappable via DI without code changes
- [ ] Business logic tests use mock implementations (no real cloud calls)
- [ ] Error types are domain-specific (not provider error classes)
- [ ] Connection status monitored but never blocks core features

## Provider Swap Scenarios

| Scenario | Auth | Sync | AI | Storage |
|----------|------|------|----|---------|
| Full cloud (Supabase) | Supabase | Supabase | Claude | Supabase |
| Full cloud (Firebase) | Firebase | Firestore | Claude | Firebase |
| Self-hosted | Custom REST | Custom REST | Claude | S3 |
| Offline-only | Local | NoOp | Rule-based | Local |
| Mixed | Supabase | NoOp | Claude | Local |

All configurations work without changing a single line of domain or presentation code.
