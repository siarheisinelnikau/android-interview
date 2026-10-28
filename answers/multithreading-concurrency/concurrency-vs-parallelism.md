# Concurrency vs. parallelism. Why must UI work stay on the main thread?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Middle · **Topic:** Multithreading/Concurrency

## Answer

Concurrency means multiple tasks can make progress during overlapping lifetimes. Parallelism means work executes simultaneously on different execution resources. Several coroutines on one thread can be concurrent without being parallel.

Android's View toolkit is generally confined to the main thread; access from arbitrary threads violates its threading contract. The main thread also processes input and frame work, so long computations or blocking calls delay interaction and rendering.

Move CPU-heavy work to an appropriate dispatcher and blocking I/O to one intended for blocking operations, then publish results safely to the UI. Starting a coroutine on the main dispatcher does not automatically move its body elsewhere. Compose state and runtime internals have additional concurrency rules; they do not permit arbitrary View access.

## References

- [Android: processes and threads](https://developer.android.com/guide/components/processes-and-threads)
