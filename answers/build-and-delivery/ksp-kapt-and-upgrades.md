# Compare KSP and kapt. How would you check processor compatibility when upgrading Kotlin and the Android Gradle Plugin?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Middle · **Topic:** Build and Delivery · **Reviewed:** 2026-10-29

## Answer

kapt generates Java-like stubs from Kotlin and runs Java annotation processors over them. KSP provides Kotlin-aware symbol processing without relying on the same stub-generation approach. A processor must explicitly support KSP; changing the dependency configuration name alone does not migrate a Java processor.

For current toolchains, distinguish KSP2 from KSP1: the maintainers have removed KSP1 and no longer support it. kapt is in maintenance mode. Check the processor, KSP implementation, Kotlin compiler, Android Gradle Plugin, and related generated-code libraries as a compatible set. A newer compiler does not guarantee every compiler plugin or processor supports it. Inspect incremental-processing support and generated API changes as well as whether a clean build succeeds.

Migrate one processor at a time when possible, remove obsolete duplicate processing, and build representative variants. Measure incremental builds too: a successful clean build can hide stale generated output or broken invalidation behavior.

## References

- [Kotlin: kapt](https://kotlinlang.org/docs/kapt.html)
- [KSP: overview and supported processing model](https://kotlinlang.org/docs/ksp-overview.html)
- [KSP maintainers: KSP1 deprecation and KSP2 migration](https://github.com/google/ksp#a-note-on-ksp1)
- [Android: built-in Kotlin and legacy kapt](https://developer.android.com/build/migrate-to-built-in-kotlin)
- [Android: kapt maintenance status and processor migration](https://developer.android.com/build/migrate-to-ksp)
