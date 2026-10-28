# What happens to the large-screen orientation and resizability opt-out when targeting API 37? How would you verify adaptive behavior?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 17 (API 37) · **Reviewed:** 2026-10-28

## Answer

For apps targeting API 37 on Android 17, the temporary opt-out from large-screen orientation, resizability, and aspect-ratio behavior introduced with API 36 is no longer available. Keeping the old manifest restriction is not a reliable strategy for preserving a portrait-only UI.

Exercise the application in resizable windows and on large displays, including recreation while editing, navigation between panes, fold/unfold changes, and external keyboard use. Verify both the visual layout and the continuity of state.

Choose adaptive layouts from available window dimensions, retain selection separately from the pane arrangement, and keep dialogs and actions reachable. Use the documented scope and exceptions rather than assuming every small display suddenly adopts the same large-screen behavior.

## References

- [Android 17: large-screen compatibility changes](https://developer.android.com/about/versions/17/behavior-changes-17)
