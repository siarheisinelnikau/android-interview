# Compare `flatMapConcat`, `flatMapMerge`, and `flatMapLatest`.

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

flatMapConcat collects each inner flow sequentially, preserving outer order. flatMapMerge collects multiple inner flows with a concurrency limit and can interleave their values. flatMapLatest cancels the previous inner collection when a new outer value arrives.

Use sequential flattening for operations whose order is part of correctness, bounded merging for independent work, and latest flattening for replacing obsolete results such as a changed search query. Check the exact library's opt-in requirements for these operators.

Concurrency limits, buffering, and error placement affect behavior beyond the operator name. One unhandled inner failure can terminate the outer pipeline. Cancellation does not undo already completed external effects, so flatMapLatest is not a safe strategy for dropping old purchase or upload operations merely because a new UI input arrived.

## References

- [kotlinx.coroutines: flatMapConcat](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/flat-map-concat.html)
- [kotlinx.coroutines: flatMapMerge](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/flat-map-merge.html)
- [kotlinx.coroutines: flatMapLatest](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/flat-map-latest.html)
