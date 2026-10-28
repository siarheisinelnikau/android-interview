# How would you use Credential Manager for passwords, passkeys, and federated sign-in? Where should authentication be verified?

[Back to questions](../../README.md#security-and-privacy)

**Level:** Middle · **Topic:** Security and Privacy

## Answer

Credential Manager provides a unified user-facing integration for supported passwords, passkeys, and federated sign-in options. The app requests an appropriate credential and handles user cancellation or unavailable providers as normal outcomes.

For passkeys, obtain a fresh challenge and relying-party options from the backend, invoke the platform flow, and send the response back for server verification. The backend validates the challenge, relying-party/origin association, signature, and relevant anti-replay/account rules. Federated tokens likewise require issuer, audience, signature, and other applicable checks.

Do not treat receiving a client-side result as proof that every backend operation is authorized. Establish the app's session only after verification, and keep authorization tied to the server-side user. Domain association, credential selection, authentication, and resource authorization are related but distinct contracts.

## References

- [Android: Credential Manager](https://developer.android.com/identity/credential-manager)
- [Android: passkey authentication](https://developer.android.com/identity/passkeys/sign-in-with-passkeys)
