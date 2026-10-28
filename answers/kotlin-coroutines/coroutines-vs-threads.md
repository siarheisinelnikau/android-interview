# What are coroutines, and how do they differ from threads?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Junior · **Topic:** Kotlin Coroutines

## Answer

A coroutine is a computation that can suspend and later resume, with its continuation managed by the coroutine machinery. A thread is an operating-system execution resource. Many suspended coroutines can share a small number of threads because suspension does not normally occupy a thread waiting for a result.

Coroutines still need threads to execute code. A blocking call blocks whichever thread is executing it, and CPU-heavy work does not become cheap merely because it runs inside launch.

Choose a dispatcher and scope appropriate to the workload and owner. Structured concurrency helps cancellation, completion, and error propagation, while thread pools control execution resources. Coroutines can improve composition of asynchronous work without automatically making it parallel, thread-safe, or persistent across process death.

## References

- [kotlinx.coroutines: core concepts](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/)
