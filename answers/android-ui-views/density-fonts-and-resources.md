# Explain `dp`, `sp`, and resource qualifiers. How do font scaling and localization affect layouts?

[Back to questions](../../README.md#android-ui-views)

**Level:** Junior · **Topic:** Android UI (Views)

## Answer

`dp` describes density-independent layout size; `sp` is intended for text and incorporates user font scaling. Convert using the platform's appropriate APIs rather than assuming that font scaling is always a single linear multiplier.

Resource qualifiers select alternatives such as locale, available width, orientation, and density. A layout that works in one locale may fail with longer translated strings, right-to-left text, or enlarged fonts. Avoid fixed heights around text and leave room for wrapping.

Use logical start/end directions and plural resources where appropriate. Test combinations, not only defaults: a narrow window with a long translation and large text is a useful stress case. Density buckets do not replace adapting to the actual available window size.

## References

- [Android: support different pixel densities](https://developer.android.com/training/multiscreen/screendensities)
- [Android: app resources](https://developer.android.com/guide/topics/resources/providing-resources)
