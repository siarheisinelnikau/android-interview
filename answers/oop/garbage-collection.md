# How does Garbage Collection work? Can unreachable objects with circular references be collected?

[Back to questions](../../README.md#oop)

**Level:** Middle · **Topic:** OOP

## Answer

A tracing garbage collector starts at GC roots, such as reachable thread stacks and runtime-held references, and follows strong references. Objects that cannot be reached are eligible for collection, including an entire unreachable cycle. Reference counting alone has difficulty with cycles; tracing collectors do not require every reference count to reach zero.

An Android leak usually means an unwanted object is still reachable: a singleton holding an Activity keeps that Activity and its View tree alive. The collector cannot infer that the application no longer needs them.

Collection timing is not deterministic. Release files, cursors, registrations, and other external resources explicitly; do not rely on collection to run cleanup. Heap dumps and paths to GC roots help find retention.

## References

- [Android: memory management](https://developer.android.com/topic/performance/memory-overview)
