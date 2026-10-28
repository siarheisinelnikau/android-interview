# How do you distinguish Android behavior changes affecting all apps from changes gated by `targetSdk`? How would you test both?

[Back to questions](../../README.md#android-core)

**Level:** Senior · **Topic:** Android Core

## Answer

An all-apps change applies because the device runs a particular OS, even if the app keeps its old target SDK. A target-gated change additionally requires the app to target a specified API level. The relevant conditions must be read separately for each change.

Test the existing production build on the new OS first. Then test a build with the new target on that OS, plus supported older OS versions. This separates device regressions from changes activated by the target upgrade.

Use the app compatibility framework to toggle supported changes individually and reproduce failures, without assuming every change has a toggle. Record dependencies, permissions, and lifecycle conditions so SDK owners can reproduce failures. Lowering the target is not a substitute for fixing an all-apps incompatibility.

## References

- [Android: compatibility testing and debugging](https://developer.android.com/guide/app-compatibility/test-debug)
