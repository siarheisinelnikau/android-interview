# Read-only vs. mutable collections. Why is `List<T>` not a guarantee of immutability?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

`List<T>` exposes reading operations; `MutableList<T>` additionally exposes mutation. A read-only reference does not prove that the backing list cannot change through another alias.

```kotlin
val mutable = mutableListOf("a")
val view: List<String> = mutable
mutable.add("b") // view now contains b too.
```

A copied list snapshot separates structural changes from the original, but nested mutable elements can still be shared. Persistent immutable collections provide a stronger structural contract and support new versions with shared implementation structure.

Expose read-only APIs when callers should not mutate, then decide separately how the implementation owns data. Do not rely on casting a read-only interface to mutate it: concrete implementations vary and may reject mutation. Neither read-only typing nor copying alone solves concurrent element mutation.

## References

- [Kotlin: collection interfaces](https://kotlinlang.org/docs/collections-overview.html)
- [Kotlin: immutable collections API](https://kotlinlang.org/api/kotlinx.collections.immutable/)
