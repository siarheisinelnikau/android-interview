# How would you represent loading, content, empty, and error states without allowing invalid combinations?

[Back to questions](../../README.md#patterns-and-architecture)

**Level:** Middle · **Topic:** Patterns and Architecture

## Answer

Represent mutually exclusive states with a type that cannot express contradictory combinations. Several unrelated booleans can accidentally produce loading, success, and fatal error simultaneously.

```kotlin
sealed interface FeedState {
    data object Loading : FeedState
    data object Empty : FeedState
    data class Content(val items: List<Item>) : FeedState
    data class Failed(val message: String) : FeedState
}
```

This is only one valid model. If refreshing existing content and showing a recoverable error are legitimate together, model those as explicit sub-states of Content rather than forbidding them. Keep errors actionable and avoid storing raw framework exceptions as the entire UI contract. Test transitions, including retries and stale responses, not just each isolated state.

## References

- [Android: UI state production](https://developer.android.com/topic/architecture/ui-layer/state-production)
- [Kotlin: sealed types](https://kotlinlang.org/docs/sealed-classes.html)
