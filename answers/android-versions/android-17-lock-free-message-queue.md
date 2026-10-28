# How does the lock-free `MessageQueue` implementation for apps targeting API 37 affect code or SDKs that inspect private queue internals?

[Back to questions](../../README.md#android-versions)

**Level:** Senior · **Topic:** Android Versions · **Version:** Android 17 (API 37) · **Reviewed:** 2026-10-29

## Answer

Apps targeting API 37 on Android 17 receive a lock-free MessageQueue implementation intended to reduce contention around queued main-thread work. Public Looper/Handler use remains the supported contract; private linked-list details do not.

Code reflecting on `mMessages` can break: under the new implementation that field remains for compatibility but is always null, even when work is pending. This can also break outdated test-idleness detection.

Search app and SDK code for queue reflection, update test dependencies, and use supported testing APIs. The guidance identifies Espresso 3.7.0+ and Robolectric 4.17+ with PAUSED Looper mode as migration points. Use the documented compatibility toggle to isolate a regression, then remove the unsupported dependency rather than treating the old queue representation as an API.

## References

- [Android 17: MessageQueue migration guidance](https://developer.android.com/about/versions/17/changes/messagequeue)
