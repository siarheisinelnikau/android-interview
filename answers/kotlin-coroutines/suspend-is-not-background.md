# What does `suspend` mean? Does a suspending function automatically run on a background thread?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Junior · **Topic:** Kotlin Coroutines

## Answer

`suspend` marks a function that can suspend in a coroutine-compatible call chain. It does not select a dispatcher, create a thread, or require that every invocation actually suspends.

```kotlin
suspend fun checksum(bytes: ByteArray): Long =
    expensiveChecksum(bytes) // Still executes on the caller's context.
```

A suspending API should be main-safe when its contract is intended for UI callers: move blocking I/O or expensive computation into a suitable context inside the implementation. A genuinely asynchronous library call may already perform its operation without blocking the caller's thread.

Suspension releases the thread only at an actual suspension point. Until then, code executes normally. Never assume that adding suspend to a blocking function protects the main thread from ANRs.

## References

- [Android: main-safe suspend functions](https://developer.android.com/kotlin/coroutines/coroutines-best-practices)
