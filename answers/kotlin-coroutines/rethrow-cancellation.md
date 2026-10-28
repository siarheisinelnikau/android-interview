# Why should `CancellationException` usually be rethrown? How can `runCatching` or a broad `catch` break cancellation?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

CancellationException normally signals that the caller no longer wants the operation. If a broad catch or runCatching converts it to an ordinary fallback and continues, the code can delay shutdown, display obsolete errors, or perform work after its owner has ended.

```kotlin
val result = try {
    repository.load()
} catch (e: CancellationException) {
    throw e
} catch (e: IOException) {
    LoadResult.NetworkError(e)
}
```

Catch only failures you can handle. Cleanup still belongs in finally or an equivalent resource owner, and should not require changing cancellation into success. Some deliberately designed APIs may translate cancellation at an explicit boundary, but that must be part of their contract; it is not a blanket justification for swallowing every Throwable.

## References

- [kotlinx.coroutines: CancellationException](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-cancellation-exception/)
- [Kotlin: runCatching catches Throwable](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/run-catching.html)
