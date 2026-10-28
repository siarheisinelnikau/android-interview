# How does `use` manage a closeable resource when a block returns early or throws? Why can a lazily consumed `Sequence` escape the resource's lifetime?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

`use` runs a block with a closeable resource and closes it on normal completion, an early return, or an exception. Supported implementations also preserve the relationship between a primary failure and a failure during cleanup.

A lazy Sequence can escape the block without having consumed the resource:

```kotlin
// Wrong: iteration happens after the reader has closed.
fun lines(path: Path): Sequence<String> =
    Files.newBufferedReader(path).use { it.lineSequence() }
```

Consume the sequence inside `use`, return a materialized result when appropriate, or expose an API that explicitly owns the resource during consumption. Be careful with sequences backed by cursors or streams as well. A lazy pipeline's creation and execution are separate moments; lexical appearance alone does not guarantee a valid resource lifetime.

## References

- [Kotlin: use](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.io/use.html)
- [Kotlin: lineSequence](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.io/line-sequence.html)
