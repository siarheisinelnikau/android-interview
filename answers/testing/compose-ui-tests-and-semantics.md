# How would you test Compose UI using semantics, user actions, and assertions? When do merged and unmerged semantics trees matter?

[Back to questions](../../README.md#testing)

**Level:** Middle · **Topic:** Testing

## Answer

Write a UI test in terms of visible state and user actions: set content with controlled dependencies, find a meaningful node, perform an action, and assert the resulting UI. Semantics expose labels, roles, state, and supported actions to the testing API.

```kotlin
rule.onNodeWithText("Retry").performClick()
rule.onNodeWithText("Loaded").assertIsDisplayed()
```

The merged semantics tree represents combined user-facing components; the unmerged tree exposes lower-level nodes when a targeted test truly needs them. Prefer stable semantics over brittle coordinates or internal hierarchy assumptions.

Use Compose synchronization and a controlled clock for animations. External asynchronous work may require a fake, idling integration, or an explicit condition-based wait. A test tag can identify a node, but it should not replace accessible labels and actions.

## References

- [Android: Compose testing](https://developer.android.com/develop/ui/compose/testing)
- [Android: test synchronization](https://developer.android.com/develop/ui/compose/testing/synchronization)
