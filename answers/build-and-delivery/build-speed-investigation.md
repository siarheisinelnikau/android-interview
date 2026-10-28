# How would you improve build speed using measurements, module boundaries, incremental processing, and Gradle caches?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Senior · **Topic:** Build and Delivery

## Answer

Measure clean and incremental builds separately and inspect the tasks that dominate each. Slow configuration, compilation, annotation processing, resource work, and dependency downloads need different fixes.

Use supported Gradle configuration and build caches, declare custom task inputs/outputs accurately, and avoid work during configuration that prevents reuse. Keep processors incremental where supported. Module boundaries can reduce recompilation, but too many tiny modules also add configuration, wiring, and task overhead.

Compare representative edits, not only a repeated warm no-op build. Keep toolchains and plugin compatibility intentional, and verify behavior on CI as well as a developer machine. Cache hits are evidence of reuse, not proof that invalidation is correct; a fast build producing stale generated code is a regression.

## References

- [Android: optimize build speed](https://developer.android.com/build/optimize-your-build)
- [Gradle: build cache](https://docs.gradle.org/current/userguide/build_cache.html)
