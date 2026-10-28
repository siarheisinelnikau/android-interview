# How would you check 16 KB page-size compatibility when an app or a third-party SDK includes native libraries?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Senior · **Topic:** Build and Delivery

## Answer

Check the packaged app for native `.so` libraries, including those brought in indirectly by SDKs. A project written entirely in Kotlin can still distribute native code through dependencies. Pure managed-code apps without such libraries generally do not need a native rebuild for page-size alignment.

For native code, verify ELF load-segment alignment, APK packaging alignment, and runtime assumptions such as hard-coded 4096-byte page sizes. Use the documented inspection tools and a suitable current AGP/NDK combination; rebuild or update incompatible SDK libraries.

Test the actual release artifact on a 16 KB emulator or device. A manifest compatibility flag or success on a 4 KB device is not proof of native compatibility. Avoid copying a release-policy deadline into code guidance; check current distribution requirements separately from the technical compatibility test.

## References

- [Android: 16 KB page-size inspection, rebuilding, and testing](https://developer.android.com/guide/practices/page-sizes)
