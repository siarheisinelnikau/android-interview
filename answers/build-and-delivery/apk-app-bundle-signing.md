# APK vs. Android App Bundle. What does app signing protect?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Junior · **Topic:** Build and Delivery

## Answer

An APK is an installable package. An Android App Bundle is a publishing format containing code and resources from which a distribution system can generate device-specific APKs. A user does not ordinarily install an AAB directly.

Signing establishes package identity and integrity and is used to verify compatible updates. It does not encrypt application code or hide embedded secrets. With Play App Signing, distinguish the upload key used to authorize uploads from the app-signing key used for distributed app packages.

Protect signing material and recovery procedures, and test the actual distribution artifact where split delivery or native libraries matter. A locally installed universal debug APK may not expose the same packaging, signing, resource delivery, or optimization problems as the production bundle.

## References

- [Android: App Bundles](https://developer.android.com/guide/app-bundle)
- [Android: app signing](https://developer.android.com/studio/publish/app-signing)
