# What is a cold Flow? What happens when it is collected twice?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Junior · **Topic:** Kotlin Flow

## Answer

A cold Flow starts its producer for each collection. Creating the flow describes the work; applying a terminal operation normally runs it. Collecting twice can therefore repeat queries, network calls, or side effects.

```kotlin
val values = flow {
    println("started")
    emit(loadValue())
}
values.collect { consume(it) }
values.collect { consume(it) } // Runs the producer again.
```

The Flow interface itself does not guarantee that an implementation is cold: StateFlow and SharedFlow are hot subtypes. Use stateIn or shareIn when consumers should share one upstream producer, with an explicit scope and start policy. Do not add sharing merely to hide ownership mistakes; it changes lifetime, replay, error handling, and resource use.

## References

- [kotlinx.coroutines: Flow contract](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-flow/)
