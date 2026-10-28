# Compare `ViewModel`, `SavedStateHandle`, saved instance state, and persistent storage. What belongs in each?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

Use a ViewModel for screen state and business work that should survive configuration changes. Use `SavedStateHandle`, saved instance state, or a Compose saver for small values needed to reconstruct a screen after supported system restoration. Use a database, DataStore, or files for durable application data.

For an editor, the selected record ID and a small input value may be saved state; a large document or durable draft should be persisted. A repository reloads authoritative data using that ID.

Saved state is size-limited and tied to the task and save/restore lifecycle. It is not a guarantee that every last write survives an abrupt exit or that state returns after the user dismisses the task. Avoid serializing a whole repository result into a Bundle.

## References

- [Android: saving UI states](https://developer.android.com/topic/libraries/architecture/saving-states)
