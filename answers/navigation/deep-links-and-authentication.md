# Deep links vs. verified App Links. How would you handle a link that requires authentication?

[Back to questions](../../README.md#navigation)

**Level:** Middle · **Topic:** Navigation

## Answer

A deep link identifies app content through a URI. A verified Android App Link uses an HTTPS domain association checked through Digital Asset Links, improving reliable routing to the owning app. A custom-scheme link does not provide the same domain-ownership verification.

Treat URI arguments as untrusted. Parse only supported routes, validate parameters, and enforce authorization in the data/backend layer. If authentication is needed, preserve a validated pending destination, run sign-in, then continue only after success and access checks. Define cancellation and expired-content behavior.

Avoid forwarding arbitrary redirect URLs or accepting unrestricted nested intents. Test installed and uninstalled flows, failed domain verification, cold start, and an already open task. Verification decides routing ownership; it does not authenticate the person following the link.

## References

- [Android: verified App Links](https://developer.android.com/training/app-links)
- [Android: deep-link security risks](https://developer.android.com/privacy-and-security/risks/unsafe-use-of-deeplinks)
