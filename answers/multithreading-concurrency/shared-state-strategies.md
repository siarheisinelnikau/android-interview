# Thread confinement, immutable data, locks, and concurrent collections - how would you choose a strategy for shared state?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Senior · **Topic:** Multithreading/Concurrency

## Answer

Choose the smallest ownership model that protects the invariant. Immutable values remove mutation races after safe publication. Thread confinement lets one thread or actor-like owner serialize changes. Locks are useful when several operations must be atomic together. Concurrent collections protect their documented operations while permitting more concurrency.

For example, `ConcurrentHashMap.get()` followed by `put()` is not a single atomic decision; use a suitable operation such as `compute` or protect the larger transaction. An immutable map containing mutable objects does not make those objects safe.

Start by listing who may read and write the data, which changes must be observed together, and how cancellation works. Throughput alone is insufficient if the result can violate a business invariant.

## References

- [Java: ConcurrentHashMap](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/concurrent/ConcurrentHashMap.html)
