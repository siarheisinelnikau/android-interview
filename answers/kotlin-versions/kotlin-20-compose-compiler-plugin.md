# Why does the Compose compiler Gradle plugin follow the Kotlin version? What changes when migrating from the old compiler extension setup?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.0 · **Reviewed:** 2026-10-28

## Answer

From Kotlin 2.0, the Compose compiler is managed alongside Kotlin and uses the corresponding Kotlin version. Apply `org.jetbrains.kotlin.plugin.compose` to modules that compile Compose code, using the same version as the Kotlin plugin.

This replaces the older setup based on selecting a separate Compose compiler extension version through `composeOptions.kotlinCompilerExtensionVersion`. The Compose BOM still manages library versions rather than this compiler plugin.

Audit module-level configuration, compiler options, custom tasks, and any direct compiler artifacts during migration. Remove conflicting old configuration instead of layering both approaches together. Check KSP and other compiler-plugin compatibility independently, then build representative variants and inspect Compose-related reports when validating changes to generated behavior.

## References

- [Kotlin: Compose compiler migration](https://kotlinlang.org/docs/compose-compiler-migration-guide.html)
