# How do time limits for `dataSync` and `mediaProcessing` foreground services work for apps targeting API 35? How should a service handle `onTimeout()`?

[Back to questions](../../README.md#android-versions)

**Level:** Senior · **Topic:** Android Versions · **Version:** Android 15 (API 35) · **Reviewed:** 2026-10-28

## Answer

For apps targeting API 35 on Android 15, background execution time for `dataSync` and `mediaProcessing` foreground services is limited. Each type has its own cumulative allowance, documented as six hours within a 24-hour period, shared across the app's services of that type. User foreground interaction affects the timer rules.

When the allowance expires, `Service.onTimeout(int, int)` gives the service a short opportunity to stop itself. Persist progress, end work promptly, and call `stopSelf()`; ignoring the callback can cause a service failure.

Design transfers to resume safely and choose WorkManager or a user-initiated transfer API when appropriate. Use shortened test timeouts to exercise cleanup instead of waiting hours or assuming each new service instance gets a fresh budget.

## References

- [Android: foreground service timeouts](https://developer.android.com/develop/background-work/services/fgs/timeout)
