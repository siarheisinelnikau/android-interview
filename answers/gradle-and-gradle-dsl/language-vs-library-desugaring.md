# Language desugaring vs. core library desugaring - what problems do they solve, and why does a newer JVM target not make every Java API available?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Language desugaring transforms supported language/bytecode features into forms that can run on older Android runtimes. Core library desugaring additionally supplies supported implementations or rewrites for selected Java library APIs on devices that do not provide them natively.

This distinction matters for a feature such as java.time: accepting the source syntax or emitting a particular bytecode version is not proof that every called method exists on the oldest supported device. Core library desugaring also covers only a documented API set, not an entire desktop JDK or every overload of a familiar class.

Enable the supported AGP option and a compatible desugaring library version when needed, then verify the exact API's availability and behavior across the device range. Check third-party libraries as well as application code. Runtime checks and AndroidX alternatives remain necessary where desugaring does not supply the required capability.

## References

- [Android: language and core library desugaring](https://developer.android.com/studio/write/java8-support)
- [Android: supported desugared APIs](https://developer.android.com/studio/write/java8-support-table)
