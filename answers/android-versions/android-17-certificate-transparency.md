# What changes for certificate transparency when targeting API 37? How would you investigate a TLS failure without bypassing certificate checks?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 17 (API 37) · **Reviewed:** 2026-10-28

## Answer

Android 17 enables certificate transparency by default for apps targeting API 37; Android 16 offered an opt-in. CT checks whether a server certificate has the required evidence of logging in recognized public certificate logs. It complements ordinary certificate-chain and hostname validation rather than replacing them.

For a failing connection, inspect the exact exception, certificate chain, hostname, device date, trust anchors, and the app's Network Security Configuration. Reproduce with the production server and relevant Android version, including SDK-owned network stacks.

Fix certificate or configuration problems at their source. Do not install a trust-all manager or disable hostname verification. Custom trust anchors have documented CT exceptions, so enterprise/private-CA environments must be evaluated according to those rules rather than treated like public certificates.

## References

- [Android: Network Security Configuration and CT](https://developer.android.com/privacy-and-security/security-config)
- [Android 17: default CT enforcement](https://developer.android.com/about/versions/17/behavior-changes-17)
