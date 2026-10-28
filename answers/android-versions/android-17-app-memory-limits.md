# How would you investigate Android 17's app memory limits using `ApplicationExitInfo` and heap dumps? Do these limits depend on `targetSdk`?

[Back to questions](../../README.md#android-versions)

**Level:** Senior · **Topic:** Android Versions · **Version:** Android 17 (API 37) · **Reviewed:** 2026-10-29

## Answer

Android 17 introduces device-RAM-based app memory limits as an all-apps behavior, so it can affect an app without a target SDK upgrade. These limits should not be confused with only the managed-heap allocation limit.

Inspect `ApplicationExitInfo`: the documented limiter termination is reported as `REASON_OTHER` with a description containing `MemoryLimiter:AnonSwap`. Correlate exits with device class, background/foreground state, memory traces, and heap dumps. Trigger-based profiling can help collect evidence around anomalies.

Establish a baseline and inspect retained objects, native allocations, image decoding, and cache bounds. Use the memory-limiter testing controls to reproduce constrained behavior. A Java heap dump alone may not explain all process memory, so combine it with process-level measurements before choosing a fix.

## References

- [Android 17: app memory limits](https://developer.android.com/about/versions/17/behavior-changes-all)
- [Android: memory diagnostics](https://developer.android.com/topic/performance/memory)
