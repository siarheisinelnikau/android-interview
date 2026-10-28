# How would you define staged-rollout health checks and recover from a bad release? What does halting a rollout actually undo?

[Back to questions](../../README.md#production-engineering)

**Level:** Senior · **Topic:** Production Engineering · **Reviewed:** 2026-10-29

## Answer

Choose health criteria before rollout: critical journey success, crash/ANR rates, performance, and relevant backend errors, segmented by release and affected device/OS cohorts. Use enough observation time and sample size to distinguish a real regression from noisy traffic changes.

A staged rollout limits how many additional users receive an update. Halting it prevents further rollout; it does not uninstall the version from users who already received it. Recovery can require a higher-versionCode corrective update, a compatible feature kill switch, or a backend mitigation. A flag cannot repair a crash occurring before flags can be loaded.

Preserve mapping files and symbols for every artifact. Consider database and server compatibility before proposing a rollback: older code may not safely interpret newly written data. Resume only with evidence about the failure and the corrective action, not simply because the total number of complaints stopped increasing.

## References

- [Google Play: staged rollout and halting behavior](https://support.google.com/googleplay/android-developer/answer/6346149)
- [Android: application versioning](https://developer.android.com/studio/publish/versioning)
