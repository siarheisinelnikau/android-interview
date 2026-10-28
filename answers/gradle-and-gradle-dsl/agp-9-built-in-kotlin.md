# AGP 9.0 - what changes with built-in Kotlin? How should `kapt`, compiler options, and KMP modules be migrated?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

AGP 9.0 enables built-in Kotlin for Android projects by default. It replaces the kotlin-android plugin integration, so applying `org.jetbrains.kotlin.android` alongside that enabled mode is not the migration strategy. Move legacy `android.kotlinOptions` configuration to the supported `kotlin.compilerOptions` DSL.

The ordinary kotlin-kapt plugin is incompatible with built-in Kotlin. Prefer a supported KSP processor; if migration is not yet possible, the documented `com.android.legacy-kapt` plugin uses the AGP version. This does not mean an arbitrary Java processor can be converted merely by renaming its configuration.

Other Kotlin compiler plugins, such as Compose or serialization, still need compatible configuration. KMP libraries use the multiplatform plugin together with the Android KMP library plugin; do not assume built-in Kotlin replaces the entire multiplatform toolchain. Check convention plugins and third-party integrations, and treat temporary opt-outs as version-specific migration tools rather than permanent compatibility guarantees.

## References

- [Android: built-in Kotlin migration](https://developer.android.com/build/migrate-to-built-in-kotlin)
- [Android: AGP 9.0 changes](https://developer.android.com/build/releases/agp-9-0-0-release-notes)
