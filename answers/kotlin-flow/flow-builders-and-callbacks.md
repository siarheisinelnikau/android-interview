# Compare `flow`, `channelFlow`, and `callbackFlow`. Why is `awaitClose` important when adapting callbacks?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

`flow` is appropriate for sequential suspending emission in the producer's supported context. `channelFlow` supports concurrent producers using send through a channel. `callbackFlow` adapts callback-style APIs and provides thread-safe sending from those callbacks.

```kotlin
fun observe(): Flow<Value> = callbackFlow {
    val listener = Listener { value -> trySend(value) }
    source.register(listener)
    awaitClose { source.unregister(listener) }
}
```

awaitClose keeps the bridge alive and unregisters it when collection ends. Registration and unregistration must tolerate cancellation races and the source's threading rules. Check the send result and choose buffering/overflow policy deliberately; a callback may not be able to suspend when consumers are slow. Without cleanup, a finished collector can leave a listener retaining its owner.

## References

- [kotlinx.coroutines: callbackFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/callback-flow.html)
- [kotlinx.coroutines: channelFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/channel-flow.html)
