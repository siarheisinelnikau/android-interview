# How does cooperative cancellation work? What do `isActive`, `ensureActive`, and `yield` do in CPU-intensive code?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

Cancellation marks the Job and is observed by cancellable suspension points or explicit checks. It does not forcibly terminate arbitrary CPU code or interrupt every blocking call.

```kotlin
for (chunk in chunks) {
    currentCoroutineContext().ensureActive()
    processChunk(chunk)
}
```

`isActive` lets code branch on cancellation, `ensureActive` throws when cancelled, and `yield` also gives other runnable coroutines an opportunity to progress. A loop that never suspends or checks cancellation can keep occupying a thread after its owner is cancelled.

Use a cancellable library API or an appropriate interruption adapter for eligible blocking JVM operations. Cancellation can race with completion; release resources in finally/use and avoid publishing obsolete UI results merely because the expensive work eventually returned.

## References

- [kotlinx.coroutines: ensureActive](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/ensure-active.html)
- [kotlinx.coroutines: yield](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/yield.html)
