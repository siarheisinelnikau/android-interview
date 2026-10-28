# How would you audit third-party SDK permissions, data collection, and local network access when preparing a platform upgrade?

[Back to questions](../../README.md#security-and-privacy)

**Level:** Senior · **Topic:** Security and Privacy

## Answer

Inspect the merged manifest and resolved dependencies rather than only the permissions written in the app's own manifest. Identify exported components, providers initialized at startup, native libraries, background services, and network traffic introduced by SDKs.

For a platform upgrade, compare those behaviors with the all-apps and target-gated changes. Android 17 local-network enforcement, for example, can affect library traffic below the HTTP API layer. An SDK's broad network use may require an update or a system-mediated alternative rather than a new permission requested without a user-facing purpose.

Verify SDK documentation, actual runtime behavior, data destinations, and collection controls. Remove unnecessary permissions/components through supported integration settings, and test startup, denied permissions, logout, and background execution. A manifest inventory is a starting point, not proof of what data is actually collected.

## References

- [Android: SDK best practices](https://developer.android.com/guide/practices/sdk-best-practices)
- [Android: local network protections](https://developer.android.com/privacy-and-security/local-network-permission)
