# What contracts do `@Stable` and `@Immutable` declare? Why can incorrect annotations lead to stale UI?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

`@Immutable` promises that the observable public state of an instance cannot change after construction. `@Stable` permits change but promises a consistent equality contract, observable notifications for relevant public property changes, and stable public property types.

These annotations communicate a contract to the compiler; they do not freeze objects, generate notifications, or validate every possible mutation. An immutable-looking data class containing a mutable list is not automatically deeply immutable.

If you incorrectly annotate a mutable object and update an ordinary field without observable state, Compose can skip work and leave stale UI. Prefer truthful data modeling and snapshot state over adding annotations to silence a report. Stability is also only part of the skipping rules under strong skipping.

## References

- [Android: diagnose and fix stability](https://developer.android.com/develop/ui/compose/performance/stability/fix)
