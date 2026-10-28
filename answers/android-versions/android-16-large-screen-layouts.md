# How do orientation, resizability, and aspect-ratio restrictions change on large screens when targeting API 36? What should you test in a portrait-only app?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 16 (API 36) · **Reviewed:** 2026-10-28

## Answer

On large displays with smallest width of at least 600dp, Android 16 ignores many orientation, resizability, and aspect-ratio restrictions for apps targeting API 36, subject to documented exceptions. A temporary compatibility opt-out is available at that target level.

A portrait-only assumption can therefore expose stretched content, clipped dialogs, lost state during recreation, or unusable navigation. Test resizing, rotation, split screen, fold/unfold transitions, and keyboard input, with small and large font scales.

Base layout decisions on the current available window, not a permanent phone/tablet label or orientation lock. A multi-pane arrangement may be appropriate when space permits, while a compact window still needs a coherent single-pane flow. Retain state independently of a particular layout arrangement.

## References

- [Android 16: adaptive layout behavior](https://developer.android.com/about/versions/16/behavior-changes-16)
- [Android: adaptive app development](https://developer.android.com/develop/ui/compose/build-adaptive-apps)
