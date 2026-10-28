# Explain stability, skipping, and strong skipping. Why is an unstable parameter not enough to conclude that a composable cannot be skipped?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Senior · **Topic:** Jetpack Compose

## Answer

With strong skipping, restartable composables can be skippable even when parameters are unstable. Stable parameters are compared using equality, while unstable ones use instance identity. Observed state invalidation can still cause the relevant scope to recompose even when its parameters appear unchanged.

Strong skipping is enabled by default with the Compose compiler from Kotlin 2.0.20. It also broadens compiler memoization of lambdas using their captured values. Non-restartable composables are not automatically made skippable by this rule.

Therefore, an unstable parameter in a compiler report does not prove repeated execution or poor performance. Inspect actual traces and object allocation patterns. Creating a fresh unstable instance on every parent execution can defeat identity-based skipping; incorrectly hiding mutation behind a stable identity can cause correctness problems.

## References

- [Android: strong skipping rules](https://developer.android.com/develop/ui/compose/performance/stability/strongskipping)
