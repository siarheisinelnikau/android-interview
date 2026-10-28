# How would you migrate a View-based screen to Compose incrementally using `ComposeView` and `AndroidView`?

[Back to questions](../../README.md#android-ui-views)

**Level:** Middle · **Topic:** Android UI (Views)

## Answer

Use `ComposeView` to host Compose inside an existing View hierarchy. In a Fragment, choose a disposal strategy tied to the appropriate view-tree lifecycle so composition resources are released with that View, not accidentally retained across its destruction.

Use `AndroidView` to host a required legacy View inside Compose. Construct it in the factory, update properties in the update block, and use supported reset/release hooks when reusing Views or releasing external resources.

Migrate a coherent component or screen and keep one clear state owner. Test focus, keyboard behavior, theming, accessibility, insets, and scrolling across the boundary. Multiple ComposeViews that save state need stable unique IDs. Interoperability reduces migration cost, but it does not automatically reconcile competing lifecycle or navigation owners.

## References

- [Android: Compose in Views](https://developer.android.com/develop/ui/compose/migrate/interoperability-apis/compose-in-views)
- [Android: Views in Compose](https://developer.android.com/develop/ui/compose/migrate/interoperability-apis/views-in-compose)
