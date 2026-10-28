# Exceptions and `Result` - how would you model expected failures without accidentally swallowing coroutine cancellation?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

Use explicit result types or sealed outcomes when callers need to branch on expected domain failures, such as an invalid form or unavailable item. Exceptions remain useful for unexpected failures or APIs with an exception contract. `Result<T>` represents success/failure but does not by itself define which failures are expected.

`runCatching` catches Throwable, which includes coroutine cancellation. Wrapping it around suspending work and treating every failure as an ordinary error can suppress cancellation.

```kotlin
try {
    load()
} catch (e: CancellationException) {
    throw e
} catch (e: IOException) {
    showRecoverableFailure(e)
}
```

Catch only what the boundary can handle. Avoid converting fatal errors or cancellation into a successful fallback, and keep cleanup in an appropriate finally/use block.

## References

- [Kotlin: exceptions](https://kotlinlang.org/docs/exceptions.html)
- [Kotlin: runCatching](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/run-catching.html)
