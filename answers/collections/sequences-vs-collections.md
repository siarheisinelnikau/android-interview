# Eager collection operations vs. `Sequence` - when does lazy evaluation help, and when can it add overhead?

[Back to questions](../../README.md#collections)

**Level:** Middle · **Topic:** Collections

## Answer

Collection chains normally evaluate each step immediately and can allocate intermediate collections. A `Sequence` evaluates elements through the pipeline as demanded by a terminal operation.

```kotlin
val firstMatches = records.asSequence()
    .filter { it.active }
    .map { it.id }
    .take(10)
    .toList()
```

This can stop early and avoid processing the entire input. Iterator and function-call overhead can make sequences slower for short, simple workloads. Some operations, such as sorting, still need all input and buffering.

A sequence is synchronous and not a background task or a replacement for Flow. Keep resource lifetimes valid until consumption finishes, and remember that repeated iteration can repeat side effects.

## References

- [Kotlin: sequences](https://kotlinlang.org/docs/sequences.html)
