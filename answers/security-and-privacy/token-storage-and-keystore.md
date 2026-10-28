# How would you protect stored authentication tokens? What does Android Keystore provide, and how do backups and logs affect data exposure?

[Back to questions](../../README.md#security-and-privacy)

**Level:** Middle · **Topic:** Security and Privacy

## Answer

Minimize token lifetime and scope, protect transport, and store only what the app actually needs. Use app-private storage and, when the threat model requires it, encrypt sensitive stored values with a key protected by Android Keystore.

Keystore stores and operates with cryptographic keys; it is not a general database for arbitrary token strings. Hardware backing and authentication requirements depend on device support and key configuration. Account for invalidated keys, logout, reinstall, and device migration.

Review backup rules so ciphertext or credentials are not restored into an invalid or unintended security context. Redact tokens from logs, crash reports, analytics, and clipboard flows. Encryption at rest does not prevent an authorized or compromised running process from using a token; backend expiration, revocation, and authorization remain necessary.

## References

- [Android: Keystore system](https://developer.android.com/privacy-and-security/keystore)
- [Android: backup rules](https://developer.android.com/identity/data/autobackup)
