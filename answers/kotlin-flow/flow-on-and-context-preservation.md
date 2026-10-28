# How does `flowOn` affect upstream execution? Why is emitting from another context inside `flow` problematic?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

flowOn changes the context of preceding upstream operations that do not already own their execution context. It does not change the downstream collector's context. Changing dispatchers can introduce a channel boundary and buffering between producer and collector.

```kotlin
flow { emit(readBlockingFile()) }
    .flowOn(ioDispatcher)
    .collect { render(it) } // Uses the collecting context.
```

A normal flow builder preserves context for emission; switching to another context and calling emit from there violates its invariants. Use flowOn for upstream execution or channelFlow when concurrent/context-crossing senders are part of the design.

flowOn does not change the dispatcher of a separately owned StateFlow producer. Cancellation can also discard in-flight values at a context boundary, so do not treat the pipeline as a durable operation log.

## References

- [kotlinx.coroutines: flowOn](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/flow-on.html)
