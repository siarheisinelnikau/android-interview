# AGP 9.0 - what changes with built-in Kotlin? How should `kapt`, compiler options, and KMP modules be migrated?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

AGP 9.0 enables built-in Kotlin by default for Android modules. Remove `org.jetbrains.kotlin.android` when using that mode. Built-in support supplies the Android integration; it does not mean every AGP release uses the newest Kotlin compiler. Check the resolved KGP version and compiler-plugin compatibility separately.

Move `android.kotlinOptions` to `kotlin.compilerOptions`. With built-in Kotlin, `jvmTarget` defaults to `android.compileOptions.targetCompatibility`. Additional Kotlin source directories must use `android.sourceSets[...].kotlin`, rather than `kotlin.sourceSets` or the Java source directory set.

The ordinary `org.jetbrains.kotlin.kapt` plugin is incompatible with built-in Kotlin. Prefer a processor supporting KSP; otherwise use the documented `com.android.legacy-kapt` bridge with the **AGP** version. Other compiler plugins, including Compose and serialization, still need compatible setup.

KMP libraries use `org.jetbrains.kotlin.multiplatform` with `com.android.kotlin.multiplatform.library`; built-in Android Kotlin does not replace the multiplatform toolchain. Separating an Android application module from shared KMP code avoids applying `com.android.application` alongside the multiplatform plugin in one module. Audit convention plugins and third-party integrations before removing temporary opt-outs.

## References

- [Android: built-in Kotlin migration](https://developer.android.com/build/migrate-to-built-in-kotlin)
- [Android: AGP 9.0 changes](https://developer.android.com/build/releases/agp-9-0-0-release-notes)
