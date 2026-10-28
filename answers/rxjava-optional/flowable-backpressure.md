# What is `Flowable`, and how does backpressure work?

[Back to questions](../../README.md#rxjava-optional)

**Level:** Senior · **Topic:** RxJava (Optional)

## Answer

`Flowable` implements the Reactive Streams demand protocol: downstream requests a number of items, and a compliant producer respects that demand. This helps connect producers and consumers with different processing rates without requiring an unlimited queue.

A callback source that cannot slow down still needs a policy: bounded buffering, dropping, keeping the latest value, or reporting overflow. Buffering is not a solution to sustained overload; it exchanges memory and latency for temporary tolerance. Dropping payment operations is very different from dropping obsolete progress updates.

Backpressure concerns item delivery, not automatically limiting every side effect started by `flatMap`. Concurrency limits, operator prefetch, and the source's actual ability to pause must also be considered.

## References

- [RxJava: backpressure](https://github.com/ReactiveX/RxJava/wiki/Backpressure)
