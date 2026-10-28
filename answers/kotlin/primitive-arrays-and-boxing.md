# Compare `IntArray` and `Array<Int>`. Where does boxing occur, and why can it matter in a hot path?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

On the JVM, `IntArray` stores primitive integers in an `int[]`, while `Array<Int>` stores references to boxed integer values. This affects memory footprint, indirection, and the work performed in numeric loops.

```kotlin
val pixels = IntArray(1_000)
val boxed = Array(1_000) { 0 }
```

Passing primitive values through generic interfaces can introduce boxing even when a particular operation began with a primitive. Converting arrays and collections can also allocate or copy data.

Use primitive arrays for appropriate dense numeric or pixel processing, but measure a real hot path before specializing ordinary application code. An array is mutable regardless of whether its variable uses val. For array contents, use `contentEquals` or related functions rather than assuming ordinary equality compares every element.

## References

- [Kotlin: arrays and primitive arrays](https://kotlinlang.org/docs/arrays.html)
