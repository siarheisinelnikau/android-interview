# What are `Context` types? How can holding an Activity context cause a memory leak?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

A Context provides access to resources, system services, components, and other environment-specific behavior. An Activity context also carries screen-specific theming and is appropriate for operations tied to that Activity. An application context has the application's process lifetime and is suitable for many long-lived services and stores.

If a singleton retains an Activity context, it can keep the destroyed Activity and its entire View tree reachable. Retaining a View, listener, or lambda capturing the Activity can create the same problem indirectly.

Use the shortest appropriate owner and release registrations at that owner's lifecycle boundary. Replacing every Context with `applicationContext` is not a universal fix: UI inflation, themed dialogs, and window operations often require a valid UI context.

## References

- [Android: Context reference](https://developer.android.com/reference/android/content/Context)
- [Android: memory leak investigation](https://developer.android.com/studio/profile/memory-profiler)
