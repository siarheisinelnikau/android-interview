# Fakes, mocks, and stubs - how would you choose dependencies for a `ViewModel` or repository test?

[Back to questions](../../README.md#testing)

**Level:** Middle · **Topic:** Testing

## Answer

A stub supplies predetermined responses. A fake implements a simplified but working contract, such as an in-memory store. A mock verifies selected interactions or expectations. Framework terminology varies, so describe the actual behavior rather than arguing only about labels.

For ViewModel state transitions, a fake repository with controllable data and failures often makes tests clear. For a retry policy, a narrowly scoped interaction assertion may matter. Do not mock so many implementation details that a harmless refactor breaks every test.

A fake must preserve the contract relevant to the test, including ordering, cancellation, and error semantics where needed. Use integration tests to detect mismatches between the fake and the real DAO or HTTP client. Reset state between tests and avoid hidden global dependencies.

## References

- [Android: test doubles](https://developer.android.com/training/testing/fundamentals/test-doubles)
