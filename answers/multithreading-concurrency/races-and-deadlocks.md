# What are race conditions and deadlocks? How would you reproduce and investigate them?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Middle · **Topic:** Multithreading/Concurrency

## Answer

A race condition makes correctness depend on uncontrolled interleaving, such as two requests both reading and then overwriting a balance. A deadlock occurs when tasks cannot progress because each waits for resources held by another, often with inconsistent lock ordering.

Reproduce races with controlled barriers or test schedulers rather than random sleeps. Collect thread dumps and traces for hangs; inspect owners, waiters, and the full lock acquisition order. Stress tests can reveal a problem but cannot prove its absence.

Fix the invariant, not just the symptom: use atomic updates, one owner for mutable state, a consistent lock order, or a transaction. Avoid holding locks across callbacks or blocking operations that may re-enter application code.

## References

- [Oracle: thread interference](https://docs.oracle.com/javase/tutorial/essential/concurrency/interfere.html)
- [Oracle: deadlock](https://docs.oracle.com/javase/tutorial/essential/concurrency/deadlock.html)
