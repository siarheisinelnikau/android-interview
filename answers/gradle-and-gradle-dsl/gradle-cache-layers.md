# Distinguish `UP-TO-DATE` checks, the build cache, the configuration cache, and incremental task execution.

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

These mechanisms avoid different work. An up-to-date check uses declared inputs, output state, and execution history to decide that a local task does not need to run. The build cache can restore outputs for matching cacheable work, including after outputs were deleted or on another compatible machine.

The configuration cache stores the configured task graph and required execution state for reuse, avoiding ordinary configuration for a compatible request. It does not store a task's compiled output in place of the build cache.

Incremental task execution means a task that does run can process only relevant input changes when its implementation supports that behavior. The Gradle daemon primarily avoids JVM startup and warm-up costs; it is another distinct mechanism.

For a reported speedup, identify which layer produced the benefit. A second no-op build says little about a representative source edit, a cold CI checkout, or whether a task declares enough inputs to invalidate correctly.

## References

- [Gradle: incremental builds and up-to-date checks](https://docs.gradle.org/current/userguide/incremental_build.html)
- [Gradle: build cache](https://docs.gradle.org/current/userguide/build_cache.html)
- [Gradle: configuration cache](https://docs.gradle.org/current/userguide/configuration_cache.html)
