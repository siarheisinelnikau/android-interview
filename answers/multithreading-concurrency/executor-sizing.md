# When would you use an `ExecutorService`? How do pool size and queue capacity affect resource usage?

[Back to questions](../../README.md#multithreadingconcurrency)

**Level:** Middle · **Topic:** Multithreading/Concurrency

## Answer

An `ExecutorService` owns task execution resources and is useful for Java APIs, dedicated pools, and workloads with explicit queue or rejection policies. Shut down an executor when its owner finishes; otherwise threads and queued tasks can outlive the feature.

Pool sizing depends on whether tasks compute or block, device resources, and external rate limits. An unbounded queue can turn overload into excessive memory use and long latency. An unbounded pool can create too many threads. A bounded queue needs an intentional rejection or admission policy.

Coroutines can use an executor-backed dispatcher, but cancellation and executor shutdown remain separate responsibilities. Prefer existing dispatchers when isolation is unnecessary, and measure queue depth and task duration before tuning.

## References

- [Java: ThreadPoolExecutor](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/concurrent/ThreadPoolExecutor.html)
