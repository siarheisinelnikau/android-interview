# Compare MVP, MVVM, and MVI. How would you choose an approach for a screen?

[Back to questions](../../README.md#patterns-and-architecture)

**Level:** Middle · **Topic:** Patterns and Architecture

## Answer

MVP typically has a presenter issue updates through a View contract. MVVM exposes presentation state and operations from a ViewModel that the View observes. MVI commonly makes actions, state transitions, and an immutable state model explicit, often with reducer-like processing.

These labels do not guarantee a particular library, thread model, or code quality. An MVVM screen can use unidirectional flow, and an MVI implementation can still hide mutable state or lose events.

Choose based on the screen's complexity, state transitions, team conventions, and testing needs. A simple form may not need a large intent/effect framework. A complex collaborative editor may benefit from explicit transitions and replayable input. Evaluate ownership and observable behavior instead of only matching class names to a pattern acronym.

## References

- [Android: UI layer architecture](https://developer.android.com/topic/architecture/ui-layer)
