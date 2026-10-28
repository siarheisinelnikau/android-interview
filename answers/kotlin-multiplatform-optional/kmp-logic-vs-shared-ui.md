# What can be shared with Kotlin Multiplatform? How does sharing business logic differ from sharing UI with Compose Multiplatform?

[Back to questions](../../README.md#kotlin-multiplatform-optional)

**Level:** Middle · **Topic:** Kotlin Multiplatform (Optional)

## Answer

Kotlin Multiplatform compiles shared Kotlin code for several targets while allowing platform-specific implementations. Suitable shared code can include domain rules, networking abstractions, serialization, persistence integration where supported, and tests.

Sharing business logic does not require sharing the UI. An Android Compose screen and an iOS native screen can call the same shared data/domain layer. Compose Multiplatform additionally allows supported UI code to be shared, with platform-specific behavior and integrations still requiring attention.

Choose the sharing boundary from product and team needs. A platform API, accessibility behavior, lifecycle, or dependency may still need native implementation. KMP is not a way to import JVM-only Android classes into common code, and sharing more lines is not automatically a better outcome than preserving a clear platform boundary.

## References

- [Kotlin: Multiplatform introduction](https://kotlinlang.org/docs/multiplatform/get-started.html)
- [JetBrains: Compose Multiplatform](https://www.jetbrains.com/compose-multiplatform/)
