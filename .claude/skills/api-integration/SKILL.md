---
name: api-integration
description: Implements API integrations with proper error handling, caching, offline fallback, and retry logic. Use when connecting to external services.
argument-hint: "service-name"
---

# API Integration

Implements external API integrations following project patterns.

## Usage
`/api-integration <service>` — Implement integration for a specific service

## Integration Architecture

```
RemoteDataSource (API calls)
  -> Repository (error mapping, caching)
      -> UseCase (business logic)
          -> State Management (UI state)
```

## Integration Pattern

### 1. Define Abstract Interface (Domain Layer)
```
interface ExternalService {
  getData(): Promise<DomainEntity>
  sendData(input: DomainInput): Promise<Result>
}
```

### 2. Implement Data Source (Data Layer)
```
class ExternalServiceImpl implements ExternalService {
  // HTTP client, error mapping, retry logic
}
```

### 3. Wire via DI
```
container.register(ExternalService, ExternalServiceImpl)
```

## Resilience Patterns

- Retry with exponential backoff
- Proper error mapping (NetworkError -> DomainError)
- Offline queue for failed operations
- Response caching where appropriate
- All API keys via .env (never hardcoded)
- Timeout configuration per API

## Checklist for Every Integration

- [ ] Abstract interface in domain layer
- [ ] Implementation in data layer
- [ ] Error mapping to domain types
- [ ] Retry logic with backoff
- [ ] Timeout configuration
- [ ] Offline fallback
- [ ] Response caching
- [ ] API keys in .env
- [ ] Integration tests with mocked HTTP
- [ ] Documentation in .env.example
