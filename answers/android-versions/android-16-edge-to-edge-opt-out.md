# What happens to the edge-to-edge opt-out when an app targets API 36 and runs on Android 16? How does running that app on Android 15 differ?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 16 (API 36) · **Reviewed:** 2026-10-29

## Answer

When an app targets API 36 and runs on Android 16, `windowOptOutEdgeToEdgeEnforcement` no longer opts the app out of edge-to-edge. The same target-36 app running on Android 15 can still encounter Android 15's opt-out behavior.

This illustrates why target SDK alone is not a complete behavior specification: the device OS also matters. Implement insets correctly rather than depending on the flag.

Test both OS versions with system bars, cutouts, keyboard transitions, scrolling content, and mixed View/Compose screens. Ensure touch targets remain usable near navigation areas and avoid applying the same inset twice. Verify screenshots and interaction, since an apparently acceptable static layout can still hide controls when the keyboard opens.

## References

- [Android 16: edge-to-edge opt-out removal](https://developer.android.com/about/versions/16/behavior-changes-16)
