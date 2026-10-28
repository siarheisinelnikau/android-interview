# Runtime permissions - how do you handle denial, one-time grants, and permission revocation?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

Request a dangerous permission in the context of a user-visible feature, after checking whether it is already granted. Explain the need with an appropriate rationale, then use an Activity Result permission contract. A denial should leave the rest of the app usable and offer a reasonable alternative where possible.

Recheck access when the feature runs. One-time grants, settings changes, auto-reset, and platform changes mean a previous successful request is not permanent authorization. Handle permission-dependent API failures as well as the initial permission callback.

Do not infer the entire permission history from `shouldShowRequestPermissionRationale()` alone. If further requests cannot show a prompt, provide a contextual settings action rather than repeatedly launching requests. Prefer permission-free system pickers when they satisfy the use case.

## References

- [Android: request runtime permissions](https://developer.android.com/training/permissions/requesting)
- [Android: permission best practices](https://developer.android.com/training/permissions/usage-notes)
