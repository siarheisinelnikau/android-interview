# Edge-to-edge layouts and `WindowInsets` - how do you handle system bars, display cutouts, and the keyboard?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Edge-to-edge means app content can occupy the area behind system UI. WindowInsets describe regions affected by status/navigation bars, cutouts, the keyboard, and related system elements. Apply padding or layout adjustments where content or interaction needs protection.

A Scaffold can provide content padding, but callers must apply it correctly and avoid also applying equivalent insets at another ancestor. Some backgrounds should extend behind bars while controls remain within safe interaction bounds.

Test keyboard opening and closing, navigation modes, landscape cutouts, and nested layouts. Do not replace runtime insets with a hard-coded status-bar height. Insets can be consumed as they propagate, so understand ownership when combining inset-aware components. A static screenshot with the keyboard hidden is not sufficient verification.

## References

- [Android: Compose window insets](https://developer.android.com/develop/ui/compose/system/insets)
