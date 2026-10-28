# Gradle Kotlin DSL, version catalogs, and convention plugins - what problem does each solve?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Middle · **Topic:** Build and Delivery

## Answer

Gradle Kotlin DSL expresses build logic using Kotlin syntax and typed APIs. A version catalog gives dependencies and plugin coordinates consistent aliases and central version declarations; it does not automatically enforce every dependency alignment or apply configuration to modules.

A convention plugin packages repeated build behavior, such as Android library defaults, lint configuration, or test setup. This reduces copy-paste while keeping meaningful module-specific decisions visible.

```kotlin
dependencies {
    implementation(libs.kotlinx.coroutines.core)
}
```

Avoid turning a convention plugin into a hidden source of unrelated dependencies. Review resolved versions and platform/BOM constraints separately from catalog declarations. Keep build logic compatible with configuration caching and use measurements before adding complex custom tasks intended to speed up the build.

## References

- [Gradle: Kotlin DSL](https://docs.gradle.org/current/userguide/kotlin_dsl.html)
- [Gradle: version catalogs](https://docs.gradle.org/current/userguide/version_catalogs.html)
- [Gradle: convention plugins](https://docs.gradle.org/current/userguide/implementing_gradle_plugins_convention.html)
