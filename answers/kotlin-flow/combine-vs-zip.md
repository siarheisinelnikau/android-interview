# Compare `combine` and `zip`. How do they behave when sources emit at different rates?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

`combine` derives results from the latest value of each source, after all required sources have emitted at least once. It is not an event ledger: rapid updates may be coalesced, so do not require one output for every input emission. It fits screen state composed from independently changing filters, account state, and cached records.

zip pairs corresponding emissions one-to-one. A faster source waits for its partner, and the zipped flow completes when pairing can no longer continue because a source completes. It fits matching related sequences rather than continuously recalculating latest state.

For example, a new filter can be combined with the latest dataset without waiting for another dataset emission. `zip` needs a new corresponding dataset emission for each subsequent pair; if that source has already completed, the zipped flow completes too. Define initial values and empty-source behavior. Neither operator inherently creates a consistent database transaction across independent upstream sources.

## References

- [kotlinx.coroutines: combine](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/combine.html)
- [kotlinx.coroutines: zip](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/zip.html)
