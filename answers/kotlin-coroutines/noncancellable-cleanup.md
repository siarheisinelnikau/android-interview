# When is `NonCancellable` appropriate for cleanup, and what are the risks of using it for regular work?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Senior · **Topic:** Kotlin Coroutines

## Answer

A cancelled coroutine still executes finally, but a cancellable suspending cleanup operation can immediately observe cancellation. A small `withContext(NonCancellable)` block can be appropriate when that cleanup must suspend to release a resource or finish a bounded protocol step.

```kotlin
finally {
    withContext(NonCancellable) { connection.closeGracefully() }
}
```

Keep the work bounded and apply an appropriate independent timeout or fallback if the cleanup API can hang. NonCancellable does not make blocking cleanup safe for the main thread and should not protect an entire request from its owner's cancellation.

Do not launch ordinary work with NonCancellable to detach it from structured ownership. If work intentionally needs a longer lifetime, choose a separately owned scope or durable scheduler and document that contract.

## References

- [kotlinx.coroutines: NonCancellable](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-non-cancellable/)
