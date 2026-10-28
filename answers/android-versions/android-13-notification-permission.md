# How does the `POST_NOTIFICATIONS` permission affect ordinary notifications and foreground service notifications? Can a foreground service start if the permission is denied?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 13 (API 33) · **Reviewed:** 2026-10-28

## Answer

Android 13 introduces the `POST_NOTIFICATIONS` runtime permission for non-exempt notifications. For an app targeting API 33 or later, the app controls when to request it; older targets have system-controlled prompting behavior.

The permission is not required simply to start a foreground service. The service must still meet its own start restrictions and supply its required notification. If notification permission is denied, foreground-service information remains available through the system's active-apps Task Manager, while the notification is generally absent from the notification drawer. Exemptions exist for specific notification categories.

Ask at a meaningful point and handle denial without a request loop. Test permission state independently from channel settings: a granted permission does not mean every channel is enabled.

## References

- [Android: notification runtime permission](https://developer.android.com/develop/ui/views/notifications/notification-permission)
