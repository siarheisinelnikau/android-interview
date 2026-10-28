# Explain `Provider`, `Property`, `map`, `flatMap`, `convention`, and `set`. How can an early `get()` call break lazy wiring?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

A Provider represents a value that can be supplied later and may carry information about the work producing it. A Property is a configurable provider-backed value. `map` transforms a value, while `flatMap` connects to another provider without producing a nested provider.

`convention` supplies a default used unless the property is explicitly configured. `set` assigns a value or provider; setting another provider can preserve a live dependency relationship rather than taking an early snapshot.

```kotlin
val buildLabel = providers.gradleProperty("buildLabel")
    .orElse("local")
    .map { it.trim() }
```

Pass this provider into a task's input property when possible. Calling `get()` during configuration can force work, fix the value too early, or fail because the value is unavailable. Providers are not necessarily memoized computations, so transformations should be predictable and free of unrelated side effects.

## References

- [Gradle: lazy values and managed properties](https://docs.gradle.org/current/userguide/lazy_configuration.html)
