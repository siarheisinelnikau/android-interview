# Compare KSP and kapt. How would you check processor compatibility when upgrading Kotlin and the Android Gradle Plugin?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Middle · **Topic:** Build and Delivery

## Answer

kapt generates Java-like stubs from Kotlin and runs Java annotation processors over them. KSP provides Kotlin-aware symbol processing without relying on the same stub-generation approach. A processor must explicitly support KSP; changing the dependency configuration name alone does not migrate a Java processor.

Check the processor, KSP implementation, Kotlin compiler, Android Gradle Plugin, and related generated-code libraries as a compatible set. A newer compiler does not guarantee every compiler plugin or processor supports it. Inspect incremental-processing support and generated API changes as well as whether a clean build succeeds.

Migrate one processor at a time when possible, remove obsolete duplicate processing, and build representative variants. Measure incremental builds too: a successful clean build can hide stale generated output or broken invalidation behavior.

## References

- [Kotlin: kapt](https://kotlinlang.org/docs/kapt.html)
- [KSP: overview and supported processing model](https://kotlinlang.org/docs/ksp-overview.html)
