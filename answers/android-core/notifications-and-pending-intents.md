# How do notification channels and `PendingIntent`s work? How would you open the correct screen with a valid back stack?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

On Android 8.0 and later, notifications are assigned to channels that users control. Choose stable channel identities based on meaningful notification categories; recreating a channel does not override the user's settings.

A PendingIntent is a token allowing another process to execute a predefined action with the creator's identity. Prefer immutable, explicit intents unless the receiver needs supported mutation. Request codes and intent identity influence whether an existing token is reused or updated.

For ordinary app screens, build an appropriate parent stack with navigation support or TaskStackBuilder. Special-purpose activities may intentionally stand alone. Test taps when the process is not running, the Activity is stopped, or another screen is open. Distinguish these from force-stop: Android 15 cancels pending intents when the package enters its stopped state, so an old notification action is not a guaranteed relaunch path. Notification permission, channel settings, and foreground service requirements are separate conditions.

## References

- [Android: notification channels](https://developer.android.com/develop/ui/views/notifications/channels)
- [Android: notification navigation](https://developer.android.com/develop/ui/views/notifications/navigation)
