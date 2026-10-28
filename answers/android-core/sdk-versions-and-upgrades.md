# Difference between `minSdk`, `targetSdk`, and `compileSdk`. How do you prepare an app for a target SDK upgrade?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

`minSdk` sets the minimum supported platform version. `compileSdk` selects the Android API surface available during compilation. `targetSdk` declares the behavior level the app has been tested against and enables platform compatibility changes.

Compiling against a new API does not make it available on older devices. Guard calls by runtime API level or use an appropriate AndroidX compatibility API. Increasing only `compileSdk` does not enable all target-gated behavior changes.

For an upgrade, read both the all-apps and target-specific change lists, update dependencies and tooling, and test a matrix of old and new OS versions. Include background execution, permissions, storage, navigation, system bars, and third-party SDKs. Track changed behavior with concrete reproduction cases rather than only checking compilation.

## References

- [Android: SDK version declarations](https://developer.android.com/guide/topics/manifest/uses-sdk-element)
- [Android: app compatibility framework](https://developer.android.com/guide/app-compatibility/test-debug)
