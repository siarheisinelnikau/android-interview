# How would you remove duplicates from a large list while preserving order? Discuss time and memory complexity.

[Back to questions](../../README.md#algorithms)

**Level:** Middle · **Topic:** Algorithms

## Answer

Use an insertion-ordered set to keep the first occurrence of each distinct value:

```kotlin
val unique = input.toCollection(LinkedHashSet()).toList()
// For ordinary Kotlin use, input.distinct() also preserves order.
```

With suitable hashing, processing n values takes expected O(n) time and O(k) extra space for k unique values. Equality and hashing must represent the intended identity; `distinctBy { it.id }` is useful when records differ but IDs define duplicates.

For data larger than memory, use a disk-backed index or external processing and explicitly preserve encounter order. Deduplicating only adjacent items uses less memory but requires an appropriate ordering and does not solve the general problem.

## References

- [Kotlin: distinct](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/distinct.html)
- [Java: LinkedHashSet](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/LinkedHashSet.html)
