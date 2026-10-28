# When targeting API 37, why can local network access require more than the `INTERNET` permission? When can a system device picker replace broad network access?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 17 (API 37) · **Reviewed:** 2026-10-28

## Answer

On Android 17, apps targeting API 37 need `ACCESS_LOCAL_NETWORK` for broad LAN communication; `INTERNET` alone no longer authorizes that access. Restrictions apply below individual HTTP libraries, so switching from OkHttp to raw sockets does not avoid them.

Use a system-mediated picker when the task only needs a user-selected device. Supported examples include the Cast output switcher and NsdManager's service picker for appropriate mDNS discovery. Broad IoT scanning may still need the runtime permission.

Request access in context, handle denial and revocation, and audit SDK traffic as well as app code. The Android 16 opt-in used a different temporary permission arrangement; do not copy that setup into an API-37 migration without checking the current documentation.

## References

- [Android: local network permission and picker alternatives](https://developer.android.com/privacy-and-security/local-network-permission)
