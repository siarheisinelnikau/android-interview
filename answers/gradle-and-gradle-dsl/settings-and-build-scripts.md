# What belongs in `settings.gradle.kts` versus `build.gradle.kts`? How do `pluginManagement` and `dependencyResolutionManagement` differ?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Junior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

The settings script defines build-level structure, including project inclusion, included builds, plugin resolution policy, and dependency-repository policy. Project build scripts configure the plugins, dependencies, extensions, and tasks of their own projects.

`pluginManagement` controls resolution of plugins requested through the plugins DSL, including plugin repositories and supported version rules. `dependencyResolutionManagement` controls repositories, catalogs, and related policy for project dependencies. A repository listed in one area is not automatically a universal source for both kinds of resolution.

```kotlin
// settings.gradle.kts
pluginManagement {
    repositories {
        google()
        gradlePluginPortal()
    }
}
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
    }
}
include(":app", ":core")
```

An included build has its own settings and dependency boundaries. Do not assume the root build's catalog or repository configuration automatically configures every independent build used for build logic.

## References

- [Gradle: settings scripts](https://docs.gradle.org/current/userguide/settings_file_basics.html)
- [Gradle: central repository declarations](https://docs.gradle.org/current/userguide/centralizing_repositories.html)
- [Gradle: plugin management](https://docs.gradle.org/current/userguide/plugins_intermediate.html)
