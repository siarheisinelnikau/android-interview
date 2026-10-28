# Version notes

[Questions](../README.md) · [Answers](../answers/README.md)

**Reviewed: 2026-10-29.** All 270 answers were read for factual errors, misleading guarantees, and consistency between explanations and examples. Release-sensitive claims were checked against official documentation. The table records the review baseline; check the compatibility of the complete toolchain before adopting a combination of versions.

| Component | Status at review | Evidence |
| --- | --- | --- |
| Kotlin | 2.4.21 is the current stable release. Kotlin 2.5 remains an upcoming release. | [Kotlin release history](https://kotlinlang.org/docs/releases.html) |
| Android | Android 17 uses API 37. QPR previews have separate release notes; the Android answers below refer to the documented base-platform behavior. | [Android 17](https://developer.android.com/about/versions/17/) |
| Android Gradle Plugin | 9.5.0 is the current release in the API index. Its release notes specify Gradle 9.6.0 and JDK 17 minimums, with support through API 37. | [AGP release index](https://developer.android.com/reference/tools/gradle-api), [AGP 9.5 notes](https://developer.android.com/build/releases/agp-9-5-0-release-notes?hl=en) |
| Compose Runtime | 1.12.1 is stable; 1.13.0-beta02 is a preview. The 1.13 beta line requires Kotlin 2.2 or newer. | [Runtime releases](https://developer.android.com/jetpack/androidx/releases/compose-runtime) |

## Kotlin

The answers distinguish feature stabilization from the version of the compiler that first previewed a feature:

- [Core context parameters](../answers/kotlin-versions/kotlin-24-context-parameter-stability.md) are stable in 2.4. Explicit context arguments still require `-Xexplicit-context-arguments`, and related callable-reference support remains experimental.
- [Explicit backing fields](../answers/kotlin-versions/kotlin-24-explicit-backing-fields.md) and [revised annotation targets](../answers/kotlin-versions/kotlin-24-annotation-targets.md) are stable in 2.4.
- [Collection literals](../answers/kotlin-versions/kotlin-24-collection-literals.md) remain experimental with `-Xcollection-literals`.
- The [common UUID API](../answers/kotlin-versions/kotlin-24-common-uuid.md) is stable in 2.4, with documented experimental exceptions for V4/V7 generation functions.

See the [Kotlin 2.4 release notes](https://kotlinlang.org/docs/whatsnew24.html) for the feature status. A language version, API version, JVM target, Gradle's embedded Kotlin, and the Kotlin compiler used by AGP each control different things.

## Android

Read each change as a combination of device OS, target SDK, and any feature-specific conditions. In particular:

- [Android 16 job quotas](../answers/android-versions/android-16-job-quotas.md) and [Android 17 app memory limits](../answers/android-versions/android-17-app-memory-limits.md) affect all apps on those OS versions.
- Android 17's [LAN permission](../answers/android-versions/android-17-local-network-permission.md), [lock-free MessageQueue default](../answers/android-versions/android-17-lock-free-message-queue.md), [large-screen opt-out removal](../answers/android-versions/android-17-large-screen-opt-out.md), and [default certificate transparency](../answers/android-versions/android-17-certificate-transparency.md) depend on targeting API 37 or higher.
- [Android 16 edge-to-edge enforcement](../answers/android-versions/android-16-edge-to-edge-opt-out.md) also depends on the device OS: the target-36 opt-out behaves differently on Android 15 and Android 16.

The answer references link to the applicable behavior-change pages, API guides, and migration guidance.

## AGP and build tools

- [Built-in Kotlin](../answers/gradle-and-gradle-dsl/agp-9-built-in-kotlin.md) is enabled by default from AGP 9.0. Check its actual compiler version, source-set DSL, compiler options, KMP integration, and kapt migration separately.
- [New DSL and variant APIs](../answers/gradle-and-gradle-dsl/agp-variant-and-artifact-apis.md) are the default in AGP 9. The legacy DSL still has a temporary opt-out; AGP 9.4 adds module-level opt-outs. The documentation assigns mandatory migration to AGP 10.
- [KSP2](../answers/build-and-delivery/ksp-kapt-and-upgrades.md) is the supported current implementation; the maintainers have removed KSP1. kapt is in maintenance mode.
- [R8](../answers/build-and-delivery/r8-and-release-only-failures.md) has relevant AGP 9.0 keep-rule/resource-shrinking defaults and an AGP 9.1 repackaging default. Test the optimized release artifact when upgrading.
- AGP 9.5 adds [experimental automated backup/restore testing](https://developer.android.com/build/releases/agp-9-5-0-release-notes?hl=en). The documented flags are `android.experimental.testSuiteSupport=true` and `android.experimental.enableBackupTest=true`. Backup/restore testing complements [process-restoration tests](../answers/testing/recreation-vs-process-restoration-tests.md); the two exercise different lifecycles.

## Examples and illustrations

The code blocks illustrate the relevant contracts and may omit imports and application-specific declarations. This documentation review included Markdown/link validation and rendered SVG inspection; it did not compile the snippets as an Android application.

There are 15 local SVG diagrams embedded in 18 answers. They cover OOP, composition/inheritance, dependency inversion, GC roots, Android lifetimes, state restoration, UDF, Compose phases/modifiers, Job ownership, architectural dependencies, Room/Paging, and Gradle lifecycle/caches/providers. Each diagram has a text alternative, and the surrounding answer remains readable without it.
