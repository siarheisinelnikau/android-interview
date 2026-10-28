# What does `produceState` provide? How would you adapt an external data source and clean it up when the producer leaves composition?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

`produceState` adapts an asynchronous producer into Compose State. Its producer coroutine follows the call's composition identity and keys; changing a key cancels the old producer and starts a new one. Assigning `value` publishes the current result to readers.

Use it when integrating a source that is not already conveniently exposed as State or a lifecycle-collected Flow. For callback subscriptions, register within the producer and use `awaitDispose` to unregister when it ends. Suspended work should cooperate with cancellation.

Provide meaningful loading/error values and avoid launching an unowned subscription outside the producer. Equal published values can be conflated according to the applicable state policy. For an Android ViewModel's existing Flow, `collectAsStateWithLifecycle` is usually the more direct lifecycle-aware bridge.

## References

- [Android: produceState](https://developer.android.com/develop/ui/compose/side-effects#producestate)
- [Android: produceState API](https://developer.android.com/reference/kotlin/androidx/compose/runtime/package-summary)
