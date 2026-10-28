# Compare `tasks.register`, `tasks.named`, and `configureEach` with eager task creation. What accidentally realizes tasks?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

`tasks.register` creates a TaskProvider and defers creating/configuring the task until needed. `tasks.named` refers to an existing registered task without immediately retrieving the task object. `configureEach` attaches configuration that is applied as matching elements are required.

```kotlin
tasks.withType<Test>().configureEach {
    testLogging.showExceptions = true
}
```

This targets JVM Test tasks and does not require eagerly configuring every task in the collection. Eager creation, some collection operations, and calling a task provider's `get()` can defeat configuration avoidance. Prefer passing providers onward and configuring through their APIs.

Configuration actions should configure their own task rather than mutate unrelated tasks whose realization order is uncertain. Laziness improves unnecessary setup cost, but it does not replace correct task dependencies, declared inputs/outputs, or configuration-cache compatibility. Check the realized task set and measured configuration time before claiming an improvement.

## References

- [Gradle: avoiding unnecessary task configuration](https://docs.gradle.org/current/userguide/task_configuration_avoidance.html)
