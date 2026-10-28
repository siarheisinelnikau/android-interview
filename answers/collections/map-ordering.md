# Compare `HashMap`, `LinkedHashMap`, and `TreeMap`. When does iteration order matter?

[Back to questions](../../README.md#collections)

**Level:** Middle · **Topic:** Collections

## Answer

`HashMap` offers no iteration-order guarantee. `LinkedHashMap` maintains a defined encounter order, normally insertion order; its access-order mode can support an LRU-style policy. `TreeMap` sorts keys using natural ordering or a comparator and normally provides O(log n) key operations.

Choose insertion order for predictable presentation or first-seen records, sorted order for range queries, and an unordered hash map when order has no meaning. Do not rely on the order observed in one test run.

A tree comparator must reflect the intended key identity: keys comparing as zero occupy the same mapping even if their `equals` implementations disagree. None of these ordinary map types makes compound operations thread-safe.

## References

- [Java: LinkedHashMap](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/LinkedHashMap.html)
- [Java: TreeMap](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/TreeMap.html)
