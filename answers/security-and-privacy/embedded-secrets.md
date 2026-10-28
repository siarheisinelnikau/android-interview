# Why can secrets embedded in an APK be extracted? What belongs on a backend instead of in the app?

[Back to questions](../../README.md#security-and-privacy)

**Level:** Middle · **Topic:** Security and Privacy

## Answer

An APK is distributed to the user's device and can be inspected, decompiled, instrumented, or observed while running. A value embedded in code, resources, native libraries, or generated BuildConfig is not a durable secret merely because it is obfuscated.

Keep privileged service credentials and authorization decisions on a backend. A public client identifier or a restricted public API key has a different threat model from a server credential; apply server-side restrictions, quotas, and appropriate authentication rather than treating both identically.

Use short-lived user tokens and suitable public-client authentication flows. Loading a permanent secret from another client-readable endpoint only relocates the extraction point. R8, string splitting, and native code can raise inspection cost, but they do not turn an untrusted client into a secure place for a shared backend secret.

## References

- [Android: hardcoded cryptographic secrets](https://developer.android.com/privacy-and-security/risks/hardcoded-cryptographic-secrets)
