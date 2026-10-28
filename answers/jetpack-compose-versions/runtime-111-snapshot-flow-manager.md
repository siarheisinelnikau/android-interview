# Runtime 1.11 - what does experimental `SnapshotFlowManager` change when observing many `snapshotFlow` instances?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Senior · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-29

## Answer

Experimental `SnapshotFlowManager` in Runtime 1.11 allows multiple snapshotFlow observations to share management of snapshot-apply observation, reducing observer overhead when many such flows are active. It does not turn snapshotFlow into a guaranteed event log or remove its state/equality semantics.

Use an owner whose lifetime matches the observations and follow the exact experimental API's setup and cleanup contract. Do not make a global manager retain obsolete screen observers merely to reduce allocation.

Before adopting it, measure whether observer management is an actual bottleneck. A handful of flows may not justify extra coordination or experimental dependency risk. Test subscription cancellation, repeated screen creation, and memory retention, in addition to checking that values are still emitted correctly.

## References

- [Android: Compose Runtime 1.11 experimental APIs](https://developer.android.com/jetpack/androidx/releases/compose-runtime)
