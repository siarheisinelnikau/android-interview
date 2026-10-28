# Compare `derivedStateOf` and `snapshotFlow`. What problem does each solve?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

`derivedStateOf` creates Compose State derived from observed snapshot state. It is useful when inputs change more often than the meaningful derived result, such as reducing frequent scroll-position changes to whether a toolbar should be collapsed. Remember the derived state holder and avoid using it for every trivial expression.

`snapshotFlow` observes snapshot state inside a collection and exposes changes as a cold Flow. Use it to feed coroutine operators, analytics, or other non-UI processing. It observes reads performed in its block and emits according to equality semantics; the block must be free of state-writing side effects.

The first tool remains within Compose's state model; the second bridges to Flow. Neither is a guarantee that every transient change will be delivered as an event.

## References

- [Android: derivedStateOf](https://developer.android.com/develop/ui/compose/side-effects#derivedstateof)
- [Android: snapshotFlow](https://developer.android.com/develop/ui/compose/side-effects#snapshotflow)
