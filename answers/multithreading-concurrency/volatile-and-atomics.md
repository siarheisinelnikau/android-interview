# Why does `volatile` not make `counter++` atomic? When would you use atomic classes and `compareAndSet`?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Middle · **Topic:** Multithreading/Concurrency

## Answer

`counter++` reads a value, computes another value, and writes it back. Two threads can both read 5 and write 6, losing one increment. Marking the field `volatile` improves visibility but does not combine those steps atomically.

```kotlin
val counter = java.util.concurrent.atomic.AtomicInteger()
counter.incrementAndGet()
```

`compareAndSet(expected, update)` succeeds only if the current value still matches the expected value. It is useful for conditional transitions and retry loops. A failed comparison requires rereading the state and reconsidering the operation.

One atomic field does not automatically protect invariants across several fields. Prefer a lock or a single immutable state value updated atomically when those values must change together. Keep retryable update functions free of external side effects.

## References

- [Java: AtomicInteger](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/concurrent/atomic/AtomicInteger.html)
