# How do item keys and `contentType` affect state and reuse in `LazyColumn` or `LazyVerticalGrid`?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

A lazy item key identifies a logical item across insertions, removals, and moves. Stable unique keys help remembered state and item-related work stay with the correct item rather than its old position. For saveable item state on Android, use supported saveable key types.

`contentType` describes which items have compatible composition structure for reuse. Several rows can share a content type; each logical item still needs its own key.

```kotlin
items(entries, key = { it.id }, contentType = { it.kind }) {
    EntryRow(it)
}
```

Do not use a changing random key or give every structurally similar item a unique content type. Keys and types support correctness and reuse; expensive image loading, blocking binding code, or bad layout constraints can still cause jank.

## References

- [Android: lazy list keys and reuse](https://developer.android.com/develop/ui/compose/lists)
