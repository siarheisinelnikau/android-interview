# How does exception propagation differ between `launch` and `async`? When can `CoroutineExceptionHandler` handle an exception?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Senior · **Topic:** Kotlin Coroutines

## Answer

A launch coroutine reports a terminal failure through its parent or the unhandled-exception path. An async coroutine stores its failure in Deferred, and await throws that failure to the awaiting caller. This difference does not mean every async failure waits until await to affect the parent: an ordinary async child can cancel its parent immediately.

Root or supervised async work needs its result observed, while supervised launch failures need an appropriate handler or local catch. A CoroutineExceptionHandler processes failures without a normal propagation path; it is not a replacement for try/catch around a recoverable operation.

The handler runs after the coroutine has failed and cannot resume it. Catch expected failures within the operation's boundary, rethrow cancellation, and choose supervision based on whether sibling tasks are genuinely independent.

## References

- [kotlinx.coroutines: CoroutineExceptionHandler and propagation paths](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-coroutine-exception-handler/)
