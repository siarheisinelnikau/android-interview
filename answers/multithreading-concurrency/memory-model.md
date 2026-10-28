# Explain the Java Memory Model and the happens-before relationship. What guarantees do locks and `volatile` provide?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Senior · **Topic:** Multithreading/Concurrency

## Answer

The Java Memory Model defines which reads may observe which writes across threads. A happens-before relationship supplies ordering and visibility guarantees; it is stronger than simply observing that two operations happened at different wall-clock times.

An unlock of a monitor happens-before a later lock of the same monitor. A write to a volatile field happens-before a subsequent read of that field. Starting a thread and successfully joining it also establish ordering relationships. These edges can transitively publish earlier ordinary writes.

Without a valid publication mechanism, another thread need not see the expected state. `volatile` provides visibility and ordering for accesses to that field, but does not turn a sequence of operations into a transaction. Lock all participating accesses consistently.

## References

- [Java Language Specification: happens-before](https://docs.oracle.com/javase/specs/jls/se25/html/jls-17.html#jls-17.4.5)
