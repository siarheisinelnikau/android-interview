# What is recomposition, and what can trigger it?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Junior · **Topic:** Jetpack Compose

## Answer

Recomposition re-executes affected composable scopes to update the composition after relevant inputs or observed snapshot state change. A parent executing again does not necessarily mean every child must execute: eligible children may be skipped when their inputs are unchanged.

Reading state establishes an observation at the phase and scope where it is read. Changing an unobserved ordinary field does not automatically trigger recomposition. Likewise, state read only during drawing can invalidate drawing without requiring composition.

Recomposition count alone is not a performance metric. A small inexpensive recomposition can be harmless, while one blocking calculation is costly. Avoid writing state unconditionally while composing, and use tracing to identify the actual expensive work or repeated invalidation path.

## References

- [Android: composable lifecycle and recomposition](https://developer.android.com/develop/ui/compose/lifecycle)
