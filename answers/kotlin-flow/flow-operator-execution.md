# Intermediate vs. terminal operators. When does a Flow start doing work?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

Intermediate operators such as map and filter return a new Flow describing another step. Terminal operators such as collect, first, single, and toList trigger collection and produce a final effect or result.

For an ordinary cold flow, intermediate operations do not start its producer by themselves. Most sequential operators run in the collecting coroutine unless a specific operator introduces context switching or concurrency. first and other limiting operations can stop collection early through controlled cancellation.

Hot flows already have an independent lifetime, but a new transformation chain still needs a collector to process its values. launchIn starts collection in a supplied scope and returns a Job; that scope must have a meaningful owner. Do not expect simply storing a transformed Flow in a property to start requests.

## References

- [kotlinx.coroutines: flow API and terminal operations](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/)
