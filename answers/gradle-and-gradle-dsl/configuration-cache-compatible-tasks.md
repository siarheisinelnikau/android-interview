# What makes a task incompatible with the configuration cache? How should it obtain files, environment values, and Gradle services?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Task actions must not reach back into Project objects, mutable build-script state, or unsupported live JVM resources. Configure the task's explicit properties and supported service references ahead of execution so Gradle can save and restore the required state.

For example, replace execution-time `project.copy` with an injected FileSystemOperations service. Supply paths through file properties and use tracked provider APIs for external configuration values instead of hidden global reads. A provider preserves laziness, but its existence does not automatically make every captured object serializable or every task input declared.

Run with configuration caching enabled, inspect its problem report, and run again to verify reuse. Then change a relevant setting and verify correct invalidation. Do not merely suppress compatibility errors or move the same Project access behind a lambda. Build-cache correctness and configuration-cache compatibility are separate contracts and both need evidence when a plugin claims to support them.

## References

- [Gradle: configuration-cache requirements](https://docs.gradle.org/current/userguide/configuration_cache_requirements.html)
