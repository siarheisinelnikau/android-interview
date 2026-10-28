# How would you diagnose Compose jank using tracing, Layout Inspector, and compiler reports before changing stability annotations?

[Back to questions](../../README.md#performance-and-debugging)

**Level:** Senior · **Topic:** Performance and Debugging

## Answer

Reproduce the jank in a release-like app with representative data, then inspect frame and composition traces. Determine whether the cost is composition, layout, drawing, image decoding, another main-thread task, or GPU work before changing data annotations.

Layout Inspector can show actual recomposition behavior, and compiler reports explain inferred stability and skippability. An unstable parameter is not automatically the cause, especially under strong skipping. High recomposition counts can be cheap; one unnecessary expensive calculation can dominate a frame.

Fix the measured cause: move expensive work, improve lazy item identity/reuse, defer a state read to a later phase, or reduce allocation. Add `@Stable` or `@Immutable` only when their contracts are true. Re-run the same benchmark and verify that the UI still updates correctly.

## References

- [Android: Compose performance tracing](https://developer.android.com/develop/ui/compose/tooling/tracing)
- [Android: Compose stability diagnostics](https://developer.android.com/develop/ui/compose/performance/stability/diagnose)
