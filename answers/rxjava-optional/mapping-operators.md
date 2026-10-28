# Compare `map`, `flatMap`, `concatMap`, and `switchMap` using a search screen as an example.

[Back to questions](../../README.md#rxjava-optional)

**Level:** Middle · **Topic:** RxJava (Optional)

## Answer

`map` synchronously transforms each item into one result. The other operators map items into reactive sources and then flatten their emissions.

`flatMap` can subscribe to several inner sources concurrently and interleave results. `concatMap` processes them sequentially, preserving source order. `switchMap` disposes the previous inner subscription when a newer source item arrives, making it suitable for search suggestions where only the latest query matters.

Use `concatMap` for ordered writes and carefully bounded `flatMap` for independent work. `switchMap` disposal cannot undo a server-side operation already committed; avoid interpreting it as transaction rollback. Handle errors inside the appropriate inner source if one failed search should not terminate the entire query stream.

## References

- [RxJava: transformation operators](https://github.com/ReactiveX/RxJava/wiki/Transforming-Observables)
