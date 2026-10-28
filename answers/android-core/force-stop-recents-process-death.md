# Force-stop vs. removing an app from Recents vs. system-initiated process death - how do they affect state and scheduled work?

[Back to questions](../../README.md#android-core)

**Level:** Senior · **Topic:** Android Core

## Answer

System-initiated process death discards memory while leaving the app eligible for later launches and supported scheduled work. A task may be restored with saved reconstruction state. No final lifecycle callback is guaranteed.

Removing a task from Recents dismisses that task; it is not a portable equivalent of force-stop. Services and scheduled work have their own rules, and manufacturer behavior can differ. Do not base a correctness guarantee on a particular device's swipe-away behavior.

Force-stop is an explicit user action that puts the package into a stopped state and prevents ordinary background relaunch until user interaction removes that state. On Android 15, stopped-state changes also cancel pending intents. Treat this as a request to stop, not a condition to bypass. Durable data still belongs in persistent storage.

## References

- [Android: process lifecycle](https://developer.android.com/guide/components/activities/process-lifecycle)
- [Android 15: stopped package behavior](https://developer.android.com/about/versions/15/behavior-changes-all)
