# How would you investigate flaky asynchronous UI tests and choose a useful balance of unit, integration, and end-to-end coverage?

[Back to questions](../../README.md#testing)

**Level:** Senior · **Topic:** Testing

## Answer

Start by classifying the flake: uncontrolled async work, shared state, real network, animation timing, device load, or an incorrect assertion. Capture logs, screenshots, traces, random seeds, and the failed state before increasing a timeout.

Replace wall-clock sleeps with observable completion conditions or controlled schedulers. Isolate databases, files, dependency containers, and accounts between tests. Check whether the test waits for the system's actual owner rather than only for one coroutine while another dispatcher is still working.

Use many focused tests for state and business rules, integration tests for contracts between real components, and a smaller set of end-to-end tests for critical journeys. The useful balance follows failure risk and feedback cost, not a fixed percentage. Retrying a flaky test can gather evidence but should not become the permanent fix.

## References

- [Android: testing strategy](https://developer.android.com/training/testing/fundamentals/strategies)
- [Android: UI test synchronization](https://developer.android.com/training/testing/espresso/idling-resource)
