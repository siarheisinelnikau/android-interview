# Channels vs. shared flows - how do buffering, suspension, and multiple consumers affect delivery?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

A Channel transfers values between senders and receivers. With several receivers, each delivered item is normally consumed by one receiver, making it useful for a work queue. SharedFlow broadcasts to active subscribers, with configured replay and buffering behavior.

A rendezvous channel suspends send until a receiver can meet it; buffered channels allow some senders to proceed before a receiver consumes the values. Overflow and cancellation behavior must match whether items can be lost.

Neither primitive by itself means durable or exactly-once processing. A receiver can obtain an item and be cancelled before completing its side effect, and a SharedFlow without replay can discard emissions while no subscriber exists. Use persistent operation state and acknowledgment when completion must survive those boundaries.

## References

- [kotlinx.coroutines: Channel](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.channels/-channel/)
- [kotlinx.coroutines: SharedFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-shared-flow/)
