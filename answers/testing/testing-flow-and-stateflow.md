# How would you test Flow emissions, `StateFlow` conflation, cancellation, and a `stateIn` flow using `WhileSubscribed`?

[Back to questions](../../README.md#testing)

**Level:** Middle · **Topic:** Testing

## Answer

For a finite cold flow, collect its results or use first/take to assert the relevant contract. For StateFlow, often assert the current value after the controlled action rather than expecting every intermediate assignment: equal updates and fast updates can be conflated legitimately.

For stateIn with WhileSubscribed, install a collector so upstream starts. Own an infinite collector in backgroundScope or cancel it explicitly, and share the test scheduler with the system under test. Advance virtual time deliberately for debounce and stop timeouts.

Test cancellation by observing producer cleanup or stopping the owned work, not merely by asserting that no exception was displayed. Exercise slow consumers and replay behavior when they matter. Avoid adding arbitrary sleeps to make an incorrectly synchronized emission assertion pass.

## References

- [Android: Flow testing](https://developer.android.com/kotlin/flow/test)
