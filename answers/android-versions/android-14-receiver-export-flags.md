# When must a context-registered receiver specify `RECEIVER_EXPORTED` or `RECEIVER_NOT_EXPORTED`? What is the exception for system broadcasts?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 14 (API 34) · **Reviewed:** 2026-10-29

## Answer

Apps targeting API 34 or later must specify export behavior for context-registered receivers on Android 14: `RECEIVER_EXPORTED` accepts appropriate broadcasts from other apps, while `RECEIVER_NOT_EXPORTED` restricts external exposure. Use the AndroidX registration API when compatibility handling is useful.

There is an exception for a receiver registered only for system broadcasts: the platform does not require the export flag in that case. Some broadcasts originate from highly privileged applications rather than the system UID, so choose flags based on the documented sender and use permissions where appropriate.

Do not mark an application-private receiver exported merely to silence a crash. Separate filters with different exposure requirements and validate any untrusted intent data before acting on it.

## References

- [Android 14: runtime receiver export behavior](https://developer.android.com/about/versions/14/behavior-changes-14)
