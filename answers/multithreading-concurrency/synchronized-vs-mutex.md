# Compare `synchronized` and coroutine `Mutex`. What happens to the waiting thread or coroutine?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Middle · **Topic:** Multithreading/Concurrency

## Answer

`synchronized` acquires a JVM monitor and blocks the waiting thread. It is reentrant: the same thread can enter the monitor again. Keep monitor-protected work short and non-suspending.

A coroutine `Mutex` suspends a contending coroutine, allowing its thread to execute other work. It is not reentrant, and ownership is not simply the executing thread. Use `withLock` so the lock is released when the block finishes or fails.

```kotlin
private val mutex = Mutex()
suspend fun increment() = mutex.withLock { counter++ }
```

Suspension avoids occupying a waiting thread; it does not remove deadlocks or make an arbitrarily large critical section a good design. On the JVM, successful Mutex lock/unlock operations also provide documented memory-ordering guarantees.

## References

- [kotlinx.coroutines: Mutex](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.sync/-mutex/)
