# What changes for non-floating windows when an app targets API 35 on Android 15? How would you find inset and edge-to-edge regressions?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 15 (API 35) · **Reviewed:** 2026-10-28

## Answer

On Android 15, targeting API 35 enforces edge-to-edge for non-floating windows. Content can extend behind system bars and cutouts, so layouts must consume the appropriate insets instead of assuming the system always reserves that area.

Audit top bars, bottom actions, gesture regions, keyboard appearance, and screens that mix Views with Compose. Apply insets at the owner that needs them; blindly adding status-bar padding at multiple levels can double the gap. Test gesture and three-button navigation, cutouts, landscape, and an open keyboard.

Use screenshot or UI regression checks on representative screens. A temporary platform opt-out is a migration aid with version-specific availability, not a lasting layout design; Android 16 tightens that escape hatch.

## References

- [Android: edge-to-edge layouts](https://developer.android.com/develop/ui/views/layout/edge-to-edge)
- [Android 15: system UI changes](https://developer.android.com/about/versions/15/behavior-changes-15)
