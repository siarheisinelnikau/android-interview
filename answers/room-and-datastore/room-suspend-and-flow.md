# Compare a DAO `suspend` function with a DAO returning `Flow`. What causes an observable query to run again?

[Back to questions](../../README.md#room-and-datastore)

**Level:** Middle · **Topic:** Room and DataStore

## Answer

A suspending DAO method performs one asynchronous operation and returns its result. It does not continue observing later changes. A DAO returning Flow can re-run its query as the observed tables are invalidated while the flow is collected.

```kotlin
@Query("SELECT * FROM items WHERE id = :id")
suspend fun find(id: Long): Item?

@Query("SELECT * FROM items ORDER BY id")
fun observeAll(): Flow<List<Item>>
```

Invalidation is based on tables, not only the rows matching a predicate, so an unrelated change can cause another query execution. Apply `distinctUntilChanged()` when suppressing equal result values is useful. Collection ownership still matters: use lifecycle-aware collection in the UI and share upstream work when the chosen architecture requires it.

## References

- [Android: asynchronous Room queries](https://developer.android.com/training/data-storage/room/async-queries)
