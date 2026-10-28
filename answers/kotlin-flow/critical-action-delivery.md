# Why can a `SharedFlow` event be missed while the UI is stopped? What delivery guarantees would you design for a critical action?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Senior · **Topic:** Kotlin Flow

## Answer

Lifecycle-aware collection commonly stops while a screen is not active. A SharedFlow with replay zero has no obligation to save an event for the next collector, so an event emitted during that gap can be lost. Adding replay can instead cause an old action to be handled again after recreation.

For a critical operation, persist its outcome or pending status with a stable identity, expose it as state, and define acknowledgment or idempotent handling. The business side effect must be safe independently of whether a particular snackbar or navigation action was displayed.

A channel is not an automatic fix: receipt and successful handling can be separated by cancellation. Specify whether delivery is best-effort, at-least-once, or durable, and test stop/start, recreation, and process-death boundaries against that contract.

## References

- [Android: UI event delivery guidance](https://developer.android.com/topic/architecture/ui-layer/events)
- [kotlinx.coroutines: replay and absent subscribers](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-shared-flow/)
