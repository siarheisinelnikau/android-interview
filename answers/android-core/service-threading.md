# Does a `Service` run on a separate thread or in a separate process by default? How would you move blocking work off its main thread?

[Back to questions](../../README.md#android-core)

**Level:** Junior · **Topic:** Android Core

## Answer

A Service's lifecycle callbacks normally execute on the main thread of its hosting process. A Service does not create a background thread, and a separate process is used only if explicitly configured. A foreground service changes visibility and execution rules, not this threading model.

Own asynchronous work explicitly, for example with a service-owned coroutine scope that is cancelled when the service is destroyed. Use the appropriate dispatcher for blocking I/O or CPU work. Finish the service when its operation is complete.

Background-start restrictions, service types, permissions, and notification deadlines still apply. For deferrable persistent work, WorkManager is usually a better owner than an ordinary Service. Never rely on a coroutine scope alone to make work survive process death.

## References

- [Android: Service fundamentals](https://developer.android.com/guide/components/services)
