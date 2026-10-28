# How do `RecyclerView`, `ListAdapter`, and `DiffUtil` work together? What causes incorrect item updates or scroll jank?

[Back to questions](../../README.md#android-ui-views)

**Level:** Middle · **Topic:** Android UI (Views)

## Answer

RecyclerView reuses item Views, while ListAdapter uses an asynchronous differ to calculate changes between list snapshots. DiffUtil separates item identity (`areItemsTheSame`) from visible content equality (`areContentsTheSame`).

Submit a new immutable snapshot when data changes. Mutating a previously submitted list or item in place can make the old and new snapshots indistinguishable to the differ. Bind every relevant property so recycled Views do not retain old state, and resolve the current adapter position before acting on position-dependent interactions.

For jank, inspect expensive binding, image loading, repeated layout, and main-thread work before blaming diffing. Use payloads when they meaningfully reduce binding cost, and treat stable IDs as a separate identity feature rather than a replacement for correct diff callbacks.

## References

- [Android: ListAdapter](https://developer.android.com/reference/androidx/recyclerview/widget/ListAdapter)
- [Android: DiffUtil](https://developer.android.com/reference/androidx/recyclerview/widget/DiffUtil)
