# What restrictions apply to starting foreground services from `BOOT_COMPLETED` when targeting API 35? How would you redesign affected work?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 15 (API 35) · **Reviewed:** 2026-10-29

## Answer

For apps targeting API 35 on Android 15, `BOOT_COMPLETED` receivers cannot start several foreground service types, including `dataSync`, `camera`, `mediaPlayback`, `phoneCall`, and `mediaProjection`; microphone restrictions already existed earlier. Consult the exact type list and prerequisites before designing boot behavior.

After reboot, reschedule eligible persistent tasks and restore metadata without immediately starting user-facing operations. WorkManager supports persistent scheduling, but its own quotas and constraints still apply. Work that genuinely needs user initiation should wait for a user action rather than be disguised as boot recovery.

Test after a real reboot and after updates, including the app's stopped state. A receiver's short execution window is not a place to run a long synchronous transfer.

## References

- [Android 15: BOOT_COMPLETED foreground service restrictions](https://developer.android.com/about/versions/15/behavior-changes-15)
