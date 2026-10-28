# What are declarable, resolvable, and consumable configurations? How does variant-aware resolution choose an Android library variant?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

A declarable configuration is a place to state dependency requirements. A resolvable configuration describes a consumer classpath or artifact request that Gradle can resolve. A consumable configuration exposes artifacts and metadata for other projects or builds to consume. Keep these roles distinct when defining custom configurations.

Variant-aware resolution compares consumer and producer attributes and capabilities, such as usage, platform, build type, or flavor-related information. It does not select an artifact merely by finding a directory with the expected name.

A 'no matching variant' error often indicates incompatible requested attributes, unsupported target types, or a missing published variant. Inspect the producer metadata and consumer request before adding arbitrary fallbacks. Android matchingFallbacks or missingDimensionStrategy address particular build-type/flavor cases; they are not universal fixes for binary incompatibility. Resolve the intended consumer configuration rather than trying to resolve an implementation dependency bucket directly.

## References

- [Gradle: configuration roles](https://docs.gradle.org/current/userguide/declaring_configurations.html)
- [Gradle: variant-aware resolution](https://docs.gradle.org/current/userguide/variant_aware_resolution.html)
- [Android: variant dependency matching](https://developer.android.com/build/build-variants)
