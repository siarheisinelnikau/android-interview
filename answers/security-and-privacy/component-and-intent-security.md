# Exported components, mutable `PendingIntent`s, and untrusted deep-link input - what risks do they introduce?

[Back to questions](../../README.md#security-and-privacy)

**Level:** Middle · **Topic:** Security and Privacy

## Answer

An exported component can become an entry point for another app. Expose only what is needed, apply suitable permissions or caller checks, and validate every untrusted argument. An explicit destination does not make incoming data trustworthy.

A mutable PendingIntent can allow its recipient to fill or modify supported parts of an operation under the creator's identity. Prefer immutable, narrowly targeted tokens unless a documented use case requires mutation. Avoid unintentionally granting broad URI or component access.

For deep links, validate the scheme, host, route, IDs, and redirect behavior, and enforce authorization when loading data. Do not blindly forward nested intents from external input. Test malicious and malformed entry requests as well as normal links; UI navigation success is not an access-control check.

## References

- [Android: exported component risks](https://developer.android.com/privacy-and-security/risks/android-exported)
- [Android: PendingIntent security](https://developer.android.com/privacy-and-security/risks/pending-intent)
