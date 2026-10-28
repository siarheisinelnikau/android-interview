# Compare `withTimeout` and `withTimeoutOrNull`. How would you release resources on cancellation?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

`withTimeout` cancels its block and throws TimeoutCancellationException when its own deadline expires. `withTimeoutOrNull` returns null for its own timeout, making a missing timed result convenient; it does not turn unrelated failures into null.

Timeout cancellation is cooperative, so blocking or CPU code that does not cooperate may not stop exactly at the requested deadline. It is not a thread-killing watchdog.

Keep resource acquisition and cleanup in a protected lifetime, such as use or finally. Cancellation can occur around suspension and return boundaries, so avoid acquiring a resource inside a timeout and assuming the caller will always receive it before cleanup becomes their responsibility. Use supported cancellable adapters and test timeout paths with virtual time where the underlying work permits it.

## References

- [kotlinx.coroutines: withTimeout](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/with-timeout.html)
- [kotlinx.coroutines: withTimeoutOrNull](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/with-timeout-or-null.html)
