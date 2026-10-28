# How do `plugins`, `apply false`, and Kotlin DSL type-safe accessors interact? Why can an `android` block be unavailable?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Applying a plugin creates model elements such as extensions, configurations, and tasks. Declaring a plugin with `apply false` makes it available without applying it to that project; it does not create an Android extension there.

Kotlin DSL generates many type-safe accessors from the model available immediately after the plugins block. A plugin applied dynamically later may not produce an accessor usable earlier in the compiled script. An Android application and library also expose different extension types.

Use the plugins DSL where possible. In reusable plugin code, react to the relevant plugin and configure its public extension type:

```kotlin
pluginManager.withPlugin("com.android.library") {
    extensions.configure<LibraryExtension> {
        buildFeatures.buildConfig = false
    }
}
```

The example uses AGP's public `LibraryExtension` and the Kotlin DSL configure extension. Avoid replacing a missing accessor with an unsafe cast to an internal AGP implementation. Verify which plugin is actually applied and at what point its model is available.

## References

- [Gradle: Kotlin DSL accessor availability](https://docs.gradle.org/current/userguide/kotlin_dsl.html)
- [Gradle: plugin application](https://docs.gradle.org/current/userguide/plugins_intermediate.html)
