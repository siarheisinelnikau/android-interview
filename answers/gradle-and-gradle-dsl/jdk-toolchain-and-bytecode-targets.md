# Distinguish the JDK running Gradle, Java toolchains, `sourceCompatibility`, `targetCompatibility`, and Kotlin `jvmTarget`. Which determines Android API availability?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

The JDK running Gradle executes the build tool and its plugins and must satisfy their compatibility requirements. A Java toolchain selects a suitable JDK for supported compilation or related tasks; it need not be identical to the daemon's runtime.

sourceCompatibility controls supported Java source language features, while targetCompatibility and Kotlin jvmTarget control the intended bytecode levels of their respective compilers. Align related Java and Kotlin outputs and understand which plugin supplies defaults. Setting a bytecode target alone does not provide every standard-library API from that JDK on an Android device.

Android API availability depends on the compile SDK's API surface, the actual device/minSdk range, and supported compatibility/desugaring mechanisms. A build can compile successfully yet call an unavailable runtime method. Keep IDE and CI JDK selection consistent, and distinguish compilation compatibility from the Java/Kotlin versions used to compile Gradle build logic.

## References

- [Android: Java versions and JDK roles](https://developer.android.com/build/jdks)
- [Gradle: Java toolchains](https://docs.gradle.org/current/userguide/toolchains.html)
