# When do you need a custom `Saver`? Why should saved state contain small restoration inputs instead of an entire screen's data?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Use a custom Saver when a UI state type cannot be stored directly by the saved-state registry. Convert it to small supported values and restore the type from those values. `listSaver` and `mapSaver` are convenient helpers when the representation has several fields.

Save a selected item ID, scroll location, or small edit input, then reconstruct or reload the full screen data. Large payloads increase serialization cost and can contribute to Binder transaction-size failures. A saver is not a place to preserve a Context, coroutine scope, network client, or open resource.

Define defaults and compatibility if the saved representation changes. Test restoration with new instances rather than only verifying that ordinary recomposition retains the same object.

## References

- [Android: custom Compose state savers](https://developer.android.com/develop/ui/compose/state-saving)
