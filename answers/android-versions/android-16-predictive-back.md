# How does targeting API 36 on Android 16 affect legacy `onBackPressed()` and `KEYCODE_BACK` handling? Which supported APIs would you use instead?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 16 (API 36) · **Reviewed:** 2026-10-28

## Answer

For apps targeting API 36 and running on Android 16 or later, predictive-back system animations are enabled by default. Legacy `Activity.onBackPressed()` and `KEYCODE_BACK` interception are no longer the supported event path under that behavior.

Use AndroidX's back dispatcher and supported navigation integrations; in Compose, use the relevant BackHandler or predictive-back APIs for custom handling. Let the navigation owner handle ordinary stack popping rather than registering a competing callback for every composable.

A predictive gesture can be cancelled. Distinguish preview/progress work from the committed navigation action and release gesture resources correctly. Test dialogs, nested destinations, an empty back stack, and cancelled gestures. Temporary opt-outs should not replace migration to the supported callback model.

## References

- [Android: custom and predictive back navigation](https://developer.android.com/guide/navigation/custom-back/predictive-back-gesture)
- [Android 16: back handling changes](https://developer.android.com/about/versions/16/behavior-changes-16)
