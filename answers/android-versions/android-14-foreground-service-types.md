# What foreground service types and type-specific permissions must an app declare when targeting API 34? How do while-in-use permissions affect background starts?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 14 (API 34) · **Reviewed:** 2026-10-29

## Answer

When running on Android 14 and targeting API 34 or later, declare the appropriate foreground service type and its type-specific manifest permission, in addition to the base foreground-service permission. Some types also require runtime permissions or other prerequisites.

For example, declaring a location service does not by itself grant location access or permit every background start. Camera, microphone, and location services can be affected by while-in-use permission rules: a permission reported as granted does not necessarily authorize accessing the resource while the app is backgrounded.

Start from a valid user-visible flow, select the correct type when promoting the service, and stop when the task ends. Test start eligibility and resource access separately; a manifest declaration is only part of the contract.

## References

- [Android 14: foreground service types required](https://developer.android.com/about/versions/14/changes/fgs-types-required)
