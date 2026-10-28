# Groovy DSL vs. Kotlin DSL - what changes, and is the build script Kotlin version the same as the app Kotlin version?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Junior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Both DSLs configure the same Gradle model and execute build logic on the build JVM. Groovy DSL uses Groovy's more dynamic syntax; Kotlin DSL uses statically checked Kotlin scripts, typed APIs, and generated accessors where available. Neither is the language in which Gradle task outcomes are magically cached.

Gradle supplies an embedded Kotlin version for its Kotlin DSL and build-logic support. That is distinct from the Kotlin compiler/plugin used to compile application sources. Upgrading the app's Kotlin plugin does not simply replace the Kotlin compiler used to interpret `build.gradle.kts`.

Migration requires more than changing the extension: rewrite dynamic property access, method calls, plugin accessors, and typed task configuration. Mixed Groovy and Kotlin projects are supported, so migrate incrementally. Measure configuration and IDE behavior instead of assuming one syntax always makes every build faster.

## References

- [Gradle: Kotlin DSL and embedded Kotlin](https://docs.gradle.org/current/userguide/kotlin_dsl.html)
