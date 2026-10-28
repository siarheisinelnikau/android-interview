# Compare state-based text fields using `TextFieldState` with the `value`/`onValueChange` approach. How do `InputTransformation` and `OutputTransformation` differ?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

A state-based field uses `TextFieldState` to coordinate text, selection, and IME composition instead of routing every edit through a separate `value`/`onValueChange` round trip. This avoids some synchronization problems when asynchronous state processing races with keyboard edits.

`InputTransformation` validates or transforms user edits before they become accepted input state. `OutputTransformation` formats the displayed result without changing the underlying stored text, with the supported system managing the display relationship. Keep domain validation distinct from presentation formatting.

For a phone number, store a consistent underlying representation, restrict permitted input as needed, and format it for display. Do not perform network requests inside an input transformation. Check the exact Material/Foundation API version and migration guidance; state ownership and persistence remain explicit design decisions.

## References

- [Android: state-based text fields](https://developer.android.com/develop/ui/compose/text/user-input)
