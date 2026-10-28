# Compare `launch`, `async`, and `withContext`. When is concurrency actually introduced?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

`launch` starts a child coroutine and returns a Job for its lifetime. `async` starts a child that produces a Deferred result obtained with await. `withContext` runs a block in a combined context and suspends the caller until the block completes, returning its result directly.

```kotlin
coroutineScope {
    val user = async { loadUser() }
    val posts = async { loadPosts() }
    render(user.await(), posts.await())
}
```

Those children can overlap; sequential calls to two suspending functions do not introduce the same concurrency. Actual parallel execution depends on dispatchers and work.

Use async for a result that should be awaited, not merely to hide errors. An async child can still fail an ordinary parent before await. Use withContext for context switching when a separately exposed concurrent task is unnecessary.

## References

- [kotlinx.coroutines: launch](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/launch.html)
- [kotlinx.coroutines: async](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/async.html)
- [kotlinx.coroutines: withContext](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/with-context.html)
