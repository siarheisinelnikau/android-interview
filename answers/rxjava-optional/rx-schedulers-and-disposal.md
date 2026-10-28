# Difference between `subscribeOn` and `observeOn`. How do you manage subscriptions across Android lifecycles?

[Back to questions](../../README.md#rxjava-optional)

**Level:** Middle · **Topic:** RxJava (Optional)

## Answer

`subscribeOn` controls where subscription and a typical synchronous upstream source execute. `observeOn` moves downstream notifications to a scheduler, often introducing a queue. Their positions and interactions with source-specific scheduling matter; neither promises that every operation in a chain uses one thread.

For example, perform blocking work on an I/O scheduler and observe results on Android's main thread before updating Views. `subscribeOn` alone is insufficient if an expensive downstream operator is placed after a main-thread `observeOn`.

Own each subscription explicitly. A Fragment subscription that accesses binding generally belongs to the view lifecycle and must be disposed at `onDestroyView`. Recreate subscriptions when appropriate; `clear()` and permanently disposing a composite have different reuse semantics.

## References

- [RxJava: threading and schedulers](https://github.com/ReactiveX/RxJava#schedulers)
- [RxJava: CompositeDisposable source](https://github.com/ReactiveX/RxJava/blob/3.x/src/main/java/io/reactivex/rxjava3/disposables/CompositeDisposable.java)
