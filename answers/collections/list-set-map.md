# Differences between `List`, `Set`, and `Map`.

[Back to questions](../../README.md#collections)

**Level:** Junior · **Topic:** Collections

## Answer

A `List` is an ordered sequence that can contain duplicate values and supports positional access. A `Set` contains unique values according to its equality contract; iteration order depends on the implementation. A `Map` associates unique keys with values and is not itself a Kotlin `Collection`.

```kotlin
val history = listOf("a", "a", "b")
val selected = setOf("a", "b")
val names = mapOf(42 to "Ada")
```

Choose by the relationship the data represents, then by access and ordering requirements. A set should express uniqueness, not merely serve as a list with incidental deduplication. Read-only interfaces restrict mutation through that reference; they do not necessarily make the backing object immutable.

## References

- [Kotlin: collections overview](https://kotlinlang.org/docs/collections-overview.html)
