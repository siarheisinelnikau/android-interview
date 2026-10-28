# Dispatchers (`Main`, `Main.immediate`, `IO`, `Default`) - how would you make a blocking operation safe to call from the main thread?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

Main runs UI work on the main thread. Main.immediate can avoid an extra dispatch when already in the appropriate main-thread context, which can affect execution ordering and reentrancy. Default targets CPU-bound work, while IO is designed for blocking I/O and can share underlying execution resources with Default.

```kotlin
suspend fun readSettings(): String = withContext(ioDispatcher) {
    settingsFile.readText()
}
```

Inject a dispatcher when controlling execution is important for tests or isolation. Do not put long calculations on Main or assume every IO task receives a dedicated thread. Existing asynchronous network and database APIs may already handle blocking internally. Context switching adds overhead, so place it at meaningful boundaries while preserving cancellation and main-safety contracts.

## References

- [kotlinx.coroutines: Dispatchers](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-dispatchers/)
