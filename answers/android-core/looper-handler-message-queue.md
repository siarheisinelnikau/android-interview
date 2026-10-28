# How do `Looper`, `Handler`, and the main message queue work?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

A Looper repeatedly takes ready work from a thread's MessageQueue and dispatches it. A Handler targets a particular Looper and posts messages or runnable callbacks to that queue. Android prepares the main Looper for the application's main thread.

```kotlin
val handler = Handler(Looper.getMainLooper())
handler.post { renderResult() }
```

Posting queues the work; it does not create a new thread. A long callback blocks later input, lifecycle callbacks, and frame work on that thread. Delayed work runs no earlier than its scheduled readiness and may run later; it is not an exact alarm.

Queued callbacks can retain screen objects. Cancel work when its owner ends, or prefer an appropriately owned coroutine for tasks whose cancellation and lifecycle should be explicit.

## References

- [Android: Looper](https://developer.android.com/reference/android/os/Looper)
- [Android: Handler](https://developer.android.com/reference/android/os/Handler)
