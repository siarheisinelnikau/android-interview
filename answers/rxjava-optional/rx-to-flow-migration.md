# How would you migrate an RxJava chain to Coroutines and Flow while preserving cancellation, error handling, and scheduling behavior?

[Back to questions](../../README.md#rxjava-optional)

**Level:** Senior · **Topic:** RxJava (Optional)

## Answer

Migrate the behavioral contract before replacing operator names. A `Single` can become a suspending function, a multi-value source can become Flow, and Subjects require an explicit hot-stream or state-holder design.

Map ordering and concurrency deliberately: `concatMap` is usually sequential flattening, while latest-query behavior often maps to `flatMapLatest`. `flowOn` affects upstream context and is not a drop-in equivalent of every `observeOn`. Preserve inner versus outer error handling, retry policy, and resource cleanup.

Use the `kotlinx-coroutines-rx3` adapters at migration boundaries and verify that cancellation disposes subscriptions. Test slow consumers and lifecycle stop/start behavior. A Flow's suspending emission and a Flowable's request protocol are different mechanisms; buffering defaults can change observed behavior even when the happy path looks identical.

## References

- [kotlinx.coroutines: RxJava 3 integration](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-rx3/)
