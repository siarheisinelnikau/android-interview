# How do `finalizeDsl`, `beforeVariants`, `onVariants`, and artifact APIs replace `afterEvaluate` or hard-coded task names? What changes with AGP 9.0 public DSL types?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Use the Android Components lifecycle at the point where the desired model is still mutable. finalizeDsl completes supported DSL setup; beforeVariants configures builders and can disable unwanted variants before their artifacts/tasks are established. onVariants exposes created variants and provider-backed properties for task/artifact wiring.

Use the public source and artifact APIs to register generated inputs or transform outputs. Do not guess generated task names, edit intermediates in place, or assume a late afterEvaluate callback can safely mutate every earlier decision. Providers let task-produced values be resolved later without performing that work during configuration.

AGP 9.0 uses the new public DSL interfaces exclusively and removes access to old implementation types and deprecated variant APIs. Update BaseExtension/internal casts and applicationVariants-style integrations to supported public types and callbacks. Check which callbacks and artifacts support the operation in the exact AGP version; not every legacy hook has a direct replacement. Test custom plugins across the claimed AGP matrix.

## References

- [Android: extending AGP and its lifecycle](https://developer.android.com/build/extend-agp)
- [Android: AGP 9.0 public DSL migration](https://developer.android.com/build/releases/agp-9-0-0-release-notes)
