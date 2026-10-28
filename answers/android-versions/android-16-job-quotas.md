# How do Android 16's job quota changes affect WorkManager even without a target SDK upgrade? How would you diagnose stopped work?

[Back to questions](../../README.md#android-versions)

**Level:** Senior · **Topic:** Android Versions · **Version:** Android 16 (API 36) · **Reviewed:** 2026-10-28

## Answer

Android 16 changes job runtime quotas for all apps on that OS, including work scheduled through WorkManager. Work started while the app is visible, or executing alongside a foreground service, is not a universal exemption from job quotas. Keeping the old target SDK therefore does not preserve the old quota model.

Record WorkManager's stop reason, retry count, constraints, and the app's standby bucket. For direct JobScheduler work, inspect its stop reasons and pending-job diagnostics. Distinguish quota stops from missing constraints, cancellation, and application failure.

Checkpoint long operations and make repeats idempotent. Use the scheduling API appropriate to a user-initiated transfer instead of assuming that a foreground notification gives unlimited job time. Reproduce with the platform's testing controls and realistic background transitions.

## References

- [Android 16: all-apps job quota changes](https://developer.android.com/about/versions/16/behavior-changes-all)
