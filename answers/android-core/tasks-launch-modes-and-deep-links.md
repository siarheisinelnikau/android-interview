# Tasks, launch modes, and intent flags - how would you prevent duplicate screens when opening a notification or deep link?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

A task contains an Activity back stack. Default launches normally create another Activity instance. `singleTop` can deliver an intent to the existing top instance; flags such as `CLEAR_TOP` and `NEW_TASK` have different stack and task-selection effects and should not be combined blindly.

For a notification or deep link, define the expected entry destination and Back behavior first. In a single-Activity app, handle a new incoming intent through navigation rather than repeatedly constructing the same destination. Handle both initial launch and `onNewIntent` where applicable.

Use stable identifiers, deduplicate repeated navigation requests, and test cold start, warm start, and an existing task containing the destination. `singleTask` can have surprising stack-clearing behavior and is not a universal duplicate-screen fix.

## References

- [Android: tasks and back stack](https://developer.android.com/guide/components/activities/tasks-and-back-stack)
