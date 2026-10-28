# Compare `combine` and `zip`. How do they behave when sources emit at different rates?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

combine produces a result from the latest value of each source whenever a source updates, after all required sources have emitted at least once. It fits screen state composed from independently changing filters, account state, and cached records.

zip pairs corresponding emissions one-to-one. A faster source waits for its partner, and the zipped flow completes when pairing can no longer continue because a source completes. It fits matching related sequences rather than continuously recalculating latest state.

For example, combining three filter changes with one retained dataset can produce three updated views; zipping them can produce only one pair until more data arrives. Define initial values and empty-source behavior. Neither operator inherently creates a consistent database transaction across independent upstream sources.

## References

- [kotlinx.coroutines: combine](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/combine.html)
- [kotlinx.coroutines: zip](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/zip.html)
