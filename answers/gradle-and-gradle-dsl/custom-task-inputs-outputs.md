# How would you implement a deterministic custom task with declared inputs and outputs? When is `@CacheableTask` appropriate?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

A custom task should expose every value affecting its result and all outputs it owns. Use typed properties and input/output annotations so Gradle can track changes and wire producers to consumers.

```kotlin
@CacheableTask
abstract class WriteGreeting : DefaultTask() {
    @get:Input
    abstract val recipient: Property<String>

    @get:OutputFile
    abstract val outputFile: RegularFileProperty

    @TaskAction
    fun writeGreeting() {
        val target = outputFile.get().asFile
        target.parentFile.mkdirs()
        target.writeText("Hello, ${recipient.get()}", Charsets.UTF_8)
    }
}
```

Configure both properties when registering the task. The example avoids clock time, undeclared environment values, and execution-time Project access. A real task with input files also needs suitable path normalization and correct directory ownership.

`@CacheableTask` opts into output caching; it does not make nondeterministic or incomplete input declarations correct. Do not cache an operation whose purpose is an external side effect, such as publishing a release, merely because it also writes a local marker file. Test input changes and cache restoration before enabling shared cache reuse.

## References

- [Gradle: custom task implementation](https://docs.gradle.org/current/userguide/implementing_custom_tasks.html)
- [Gradle: incremental build inputs and outputs](https://docs.gradle.org/current/userguide/incremental_build.html)
