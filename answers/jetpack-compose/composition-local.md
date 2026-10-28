# Compare `compositionLocalOf` and `staticCompositionLocalOf`. When are explicit parameters preferable to a `CompositionLocal`?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

A CompositionLocal supplies a value to descendants in a portion of the composition tree. It fits pervasive environment-like values, such as theme data, better than arbitrary screen dependencies.

`compositionLocalOf` tracks reads, so changing the provided value invalidates readers. `staticCompositionLocalOf` does not track individual reads; changing its provided value invalidates the content where it is provided more broadly. The static form fits values that rarely change, not values that are globally immutable by magic.

Prefer explicit parameters when they make a component's dependency and test setup clearer. Hiding a screen ViewModel or mutable application state in a local can make reusable components difficult to reason about. Provide sensible defaults or fail clearly when a required environment value is missing.

## References

- [Android: CompositionLocal](https://developer.android.com/develop/ui/compose/compositionlocal)
