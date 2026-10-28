# How would you adapt a screen to resizable windows, tablets, and foldables using window size classes and adaptive layouts?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Adapt to the current window's available space rather than assuming an entire device is permanently a phone or tablet. Window size classes provide useful breakpoints, while fold posture and display features can add constraints beyond width alone.

A compact list/detail feature may show one destination at a time; an expanded window may show list and detail together. Keep selection, navigation history, and domain state independent from the pane arrangement so resizing does not reset the user's task.

Use adaptive layout and navigation components where they fit, then test resizing, split screen, fold/unfold, keyboard interaction, and font scaling. Avoid relying on orientation locks or an initial size read. A wide window does not automatically make every control accessible or every content column readable.

## References

- [Android: adaptive Compose apps](https://developer.android.com/develop/ui/compose/build-adaptive-apps)
- [Android: window size classes](https://developer.android.com/develop/adaptive-apps/guides/get-started-with-adaptive-apps)
