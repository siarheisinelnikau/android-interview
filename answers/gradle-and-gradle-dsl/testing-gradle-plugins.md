# How would you test a convention plugin or custom task with Gradle TestKit, including configuration-cache and build-cache behavior?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Use unit tests for isolated calculations, then TestKit functional tests to run a real fixture build with the plugin applied. GradleRunner can use the plugin-under-test classpath, selected Gradle versions, arguments, and an isolated project directory. An Android plugin fixture additionally needs a compatible SDK/toolchain.

Assert observable outputs and relevant task outcomes, not only successful exit or a printed log line. Run unchanged work twice for up-to-date behavior, change an input to prove invalidation, and use a controlled cache to test restoration after removing outputs. Enable the configuration cache and verify reuse on a second compatible invocation.

```kotlin
val result = GradleRunner.create()
    .withProjectDir(fixtureDir)
    .withPluginClasspath()
    .withArguments("writeGreeting", "--configuration-cache")
    .build()
```

The fixture must apply the plugin and configure the task's required properties. Include unsupported input and failure cases, and test the documented compatibility matrix rather than expecting one developer's warm cache to prove correctness.

## References

- [Gradle: testing build logic with TestKit](https://docs.gradle.org/current/userguide/test_kit.html)
