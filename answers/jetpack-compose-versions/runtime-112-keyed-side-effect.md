# Runtime 1.12 - when would keyed `SideEffect` replace a `LaunchedEffect` that performs no suspending work?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Middle · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-28

## Answer

Runtime 1.12 adds SideEffect overloads with keys. They can publish non-suspending external state after a successful composition when the relevant keys change, avoiding a coroutine or disposal callback that the operation does not need.

A suitable example is synchronizing a small property on an externally owned analytics object. Use LaunchedEffect when the action suspends or needs a composition-owned coroutine; use DisposableEffect when setup must be paired with teardown.

Keys describe when the action is relevant. Re-entering composition or changing identity can cause another execution, so keyed SideEffect is not an exactly-once durable delivery mechanism. Keep the work brief, and do not perform blocking I/O or a payment operation in the composition commit path.

## References

- [Android: Compose Runtime 1.12 keyed SideEffect](https://developer.android.com/jetpack/androidx/releases/compose-runtime)
