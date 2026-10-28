# Differences between `Observable`, `Single`, `Maybe`, and `Completable`.

[Back to questions](../../README.md#rxjava-optional)

**Level:** Middle · **Topic:** RxJava (Optional)

## Answer

The types express different cardinality contracts. `Observable<T>` emits zero or more values without Reactive Streams backpressure. `Single<T>` produces exactly one value or an error. `Maybe<T>` produces one value, completes empty, or fails. `Completable` reports completion or failure without a value.

An HTTP request returning a required entity often fits `Single`; an optional cache lookup fits `Maybe`; saving a record can fit `Completable`. Pick the contract callers can reason about, not a universal `Observable` for every operation.

Successful termination and failure are mutually exclusive terminal signals. These types do not inherently mean background execution or lifecycle awareness. Scheduling, disposal, cold/hot behavior, and ownership still need to be designed.

## References

- [RxJava: reactive type contracts](https://github.com/ReactiveX/RxJava#base-classes)
