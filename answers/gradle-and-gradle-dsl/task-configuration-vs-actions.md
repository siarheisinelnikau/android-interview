# What is the difference between configuring a task and adding a `doLast` or `@TaskAction`? When does each piece of code run?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

A task configuration action sets up the task object: its inputs, outputs, actions, and relationships. A task action performs the selected task's work during execution. Code placed directly inside a task configuration block is not automatically an execution action.

```kotlin
tasks.register("explainLifecycle") {
    logger.lifecycle("Task is being configured")
    doLast {
        logger.lifecycle("Task action is executing")
    }
}
```

Lazy registration means the first message appears only if the task is realized/configured; the second requires its action to execute. Configuration can occur even when the action is later skipped as up-to-date. A compatible configuration-cache hit can avoid running the configuration block again.

Put file generation and other work in a typed task action, and describe its inputs and outputs during configuration. Adding `doLast` alone does not make arbitrary captured Project objects compatible with configuration caching.

## References

- [Gradle: registering tasks and task actions](https://docs.gradle.org/current/userguide/tutorial_using_tasks.html)
- [Gradle: task configuration avoidance](https://docs.gradle.org/current/userguide/task_configuration_avoidance.html)
