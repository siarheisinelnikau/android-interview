# What do snapshot mutation policies control? How do structural equality, referential equality, and `neverEqualPolicy` affect invalidation?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Senior · **Topic:** Jetpack Compose

## Answer

A SnapshotMutationPolicy defines when old and new state values are considered equivalent and can participate in merging concurrent snapshot changes. The common policies compare structural equality, reference identity, or consider every assignment a change.

With structural equality, assigning an equal data value normally does not invalidate readers. With referential equality, a different instance can count as a change even if `equals` says it is equal. `neverEqualPolicy` treats assignments as changes regardless of equality.

A policy does not observe arbitrary in-place mutations when no state assignment occurs. Nor does it fix an incorrect equality contract. Select a policy matching the meaning of the state, and remember that using never-equal behavior can create unnecessary work without improving correctness.

## References

- [Android: SnapshotMutationPolicy](https://developer.android.com/reference/kotlin/androidx/compose/runtime/SnapshotMutationPolicy)
