# How would you design an offline-first feature with a single source of truth, optimistic updates, and conflict resolution?

[Back to questions](../../README.md#patterns-and-architecture)

**Level:** Senior · **Topic:** Patterns and Architecture

## Answer

Make local storage the read source for the UI and synchronize remote changes into it. An optimistic write updates local visible state and records a pending operation, preferably atomically. A background owner later sends that operation and reconciles the response.

Use stable operation IDs, idempotent server handling, retryable checkpoints, and an explicit pending/failed status. Network timeouts can leave the server's outcome unknown, so blind duplicate writes are unsafe. Persist the queue if work must survive process death.

Conflict resolution depends on domain rules: version checks, server-authoritative fields, merges, or user resolution may be appropriate. Last-write-wins is not universally correct, especially when clocks differ. Preserve pending local edits during refresh, define deletions and pagination, and test offline edits followed by conflicting remote changes.

## References

- [Android: offline-first data layer](https://developer.android.com/topic/architecture/data-layer/offline-first)
