---
name: offline-first
description: Implements offline-first architecture patterns — local database as source of truth, sync queue for cloud operations, conflict resolution, and graceful degradation. Use when building any data feature.
user-invocable: false
---

# Offline-First Architecture

The application is offline-first by design. The local database is the SINGLE source of truth. Cloud sync is optional and additive.

## Core Principles

### 1. Local Database is Truth
- All reads come from local database — NEVER from network
- All writes go to local database FIRST, then sync queue
- App must be 100% functional with zero network connectivity
- User never sees a "no internet" error for core features

### 2. Sync is Optional and Additive
- User explicitly opts in to cloud sync
- Sync adds: backup, multi-device, sharing
- Sync never removes: local functionality, offline access
- If sync fails, local data is unaffected

### 3. Cloud-Agnostic Sync Layer
- Abstract sync interface — not tied to any specific provider
- Repository pattern: `LocalDataSource` + `RemoteDataSource` + `SyncManager`
- Provider can be swapped without touching business logic

## Architecture

```
User Action
  -> Repository (orchestrator)
      -> LocalDataSource (DB/DAO) — ALWAYS, FIRST
      -> SyncQueue (enqueue for later) — IF sync enabled
          -> RemoteDataSource (cloud provider) — WHEN online
              -> ConflictResolver (if needed)
                  -> LocalDataSource (apply resolution)
```

### Repository Pattern (Offline-First)

```
// Pseudocode — adapt to your language/framework
interface ItemRepository {
  // All reads from local — instant, offline
  watchAll(): Stream<Item[]>
  getById(id: string): Promise<Item?>

  // All writes to local first, then sync
  create(item: Item): Promise<void>
  update(item: Item): Promise<void>
  delete(id: string): Promise<void>

  // Sync operations (optional)
  sync(): Promise<SyncResult>
  watchSyncStatus(): Stream<SyncStatus>
}

class ItemRepositoryImpl implements ItemRepository {
  localDao: ItemDao           // Local DB — always available
  remote?: RemoteDataSource   // Cloud — nullable, optional
  syncQueue: SyncQueue        // Pending operations queue

  async create(item: Item) {
    // 1. Write to local database (instant, offline)
    await localDao.insert(item)

    // 2. Enqueue for sync (if enabled)
    if (remote != null) {
      await syncQueue.enqueue('items', item.id, 'create')
    }
  }
}
```

### Conflict Resolution Strategy

```
Last-Write-Wins (default):
  - Compare updatedAt timestamps
  - Most recent write wins
  - Simple, predictable, sufficient for single-user

Field-Level Merge (optional, for shared data):
  - Compare individual fields
  - Non-conflicting changes merge automatically
  - Conflicting changes: prompt user to choose
```

## Offline-First Checklist (EVERY feature)

- [ ] All reads from local data access layer (never network)
- [ ] All writes to local first, sync queue second
- [ ] Feature works with zero network (airplane mode)
- [ ] No "loading" state waiting for network on app launch
- [ ] Sync status shown but never blocks user
- [ ] Failed sync retries with exponential backoff
- [ ] User can disable sync entirely without losing features
- [ ] No cloud provider imports in domain or presentation layers

## What NEVER Requires Network
- Viewing all local data
- Adding/editing/deleting any records
- Viewing analytics and charts
- Creating notes and documents
- All core business logic
- Full app navigation

## What MAY Use Network (When Available)
- Cloud backup/sync (user opt-in)
- AI API features (graceful fallback to rule-based)
- External data feeds (cache locally, refresh when online)
- Document processing via cloud API (on-device processing as fallback)
